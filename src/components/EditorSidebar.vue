<template>
  <div class="drawer-side z-40">
    <label for="drawer" aria-label="close sidebar" class="drawer-overlay"></label>
    <div class="menu p-4 w-80 min-h-full bg-base-200">
      <div class="space-y-4">
        <!-- Theme Selector -->
        <ThemeSelector :theme="theme" @updateTheme="$emit('updateTheme', $event)" />

        <!-- File Management -->
        <div class="divider">File Management</div>
        
        <!-- Current Languages -->
        <div v-if="languageCount > 0" class="bg-base-100 rounded-lg p-3 mb-3">
          <div class="text-xs font-semibold mb-2">Current Languages ({{ languageCount }})</div>
          <div class="space-y-1">
            <div v-for="(language, index) in languages" :key="index" class="text-xs flex items-center gap-2">
              <div class="w-2 h-2 bg-primary rounded-full"></div>
              <span>{{ language }}</span>
            </div>
          </div>
        </div>
        
        <!-- Language Column Management -->
        <div class="flex gap-1">
          <button class="btn btn-sm btn-success flex-1" @click="$emit('addLanguageColumn')">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
            </svg>
            Add
          </button>
          <button 
            class="btn btn-sm btn-error btn-outline flex-1" 
            @click="$emit('removeLanguageColumn')"
            :disabled="languageCount <= 1"
            :title="languageCount <= 1 ? 'Cannot remove the last column' : 'Remove a language column'"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
            </svg>
            Remove
          </button>
        </div>

        <!-- Project Management -->
        <div class="divider">Project</div>
        
        <!-- Save Project -->
        <div class="flex gap-1">
          <button class="btn btn-sm btn-outline flex-1" @click="$emit('saveProjectToLocalStorage')">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7H5a2 2 0 00-2 2v9a2 2 0 002 2h14a2 2 0 002-2V9a2 2 0 00-2-2h-3m-1 4l-3-3m0 0l-3 3m3-3v12" />
            </svg>
            Save
          </button>
          <button class="btn btn-sm btn-outline flex-1" @click="$emit('saveProjectToFile')">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
            </svg>
            Download
          </button>
        </div>

        <!-- Table Controls -->
        <div class="divider">Table Controls</div>
        
        <!-- Column Reset -->
        <button class="btn btn-sm btn-block" @click="$emit('resetColumnWidths')">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M4 2a1 1 0 011 1v2.101a7.002 7.002 0 0111.601 2.566 1 1 0 11-1.885.666A5.002 5.002 0 005.999 7H9a1 1 0 010 2H4a1 1 0 01-1-1V3a1 1 0 011-1zm.008 9.057a1 1 0 011.276.61A5.002 5.002 0 0014.001 13H11a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0v-2.101a7.002 7.002 0 01-11.601-2.566 1 1 0 01.61-1.276z" clip-rule="evenodd" />
          </svg>
          Reset Column Widths
        </button>

        <!-- Search Controls -->
        <SearchControls
          :searchQuery="searchQuery"
          :filteredCount="filteredCount"
          :totalKeys="totalKeys"
          :noResults="noResults"
          @update:searchQuery="$emit('update:searchQuery', $event)"
          @clearSearch="$emit('clearSearch')"
        />

        <!-- Export Controls -->
        <ExportControls
          @exportAll="$emit('exportAll')"
          @exportChanged="$emit('exportChanged')"
          @exportOriginal="$emit('exportOriginal')"
          @goBack="$emit('goBack')"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import ThemeSelector from './ThemeSelector.vue'
import SearchControls from './SearchControls.vue'
import ExportControls from './ExportControls.vue'

interface Props {
  theme: string
  searchQuery: string
  filteredCount: number
  totalKeys: number
  noResults: boolean
  languageCount: number
  languages: string[]
}

defineProps<Props>()

defineEmits<{
  updateTheme: [event: Event]
  resetColumnWidths: []
  'update:searchQuery': [value: string]
  clearSearch: []
  exportAll: []
  exportChanged: []
  exportOriginal: []
  goBack: []
  addLanguageColumn: []
  removeLanguageColumn: []
  saveProjectToLocalStorage: []
  saveProjectToFile: []
}>()
</script>
