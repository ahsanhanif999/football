<template>
    <div aria-live="assertive" class="fixed inset-0 flex items-end px-4 py-6 pointer-events-none sm:p-6 sm:items-start z-20">
      <div class="w-full flex flex-col items-center space-y-4 sm:items-end">
        <transition enter-active-class="transform ease-out duration-300 transition" enter-from-class="translate-y-2 opacity-0 sm:translate-y-0 sm:translate-x-2" enter-to-class="translate-y-0 opacity-100 sm:translate-x-0" leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
          <div v-if="show" class="max-w-sm w-full bg-white shadow-lg rounded-lg pointer-events-auto ring-1 ring-black ring-opacity-5 overflow-hidden">
            <div class="p-4">
              <div class="flex items-start">
                <div class="flex-shrink-0">
                  <CheckCircleIcon v-if="type == 'success'" class="h-6 w-6 text-themegreen" aria-hidden="true" />
                  <XCircleIcon v-else-if="type == 'error'" class="h-6 w-6 text-themered" aria-hidden="true" />
                </div>
                <div class="ml-3 w-0 flex-1 pt-0.5">
                  <p class="text-sm font-medium text-gray-900">{{message}}</p>
                  <p v-if="messageDetails != ''" class="mt-1 text-sm text-gray-500">{{messageDetails}}</p>
                </div>
                <div class="ml-4 flex-shrink-0 flex">
                  <button type="button" @click="this.$emit('close')" class="bg-white rounded-md inline-flex text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    <span class="sr-only">Close</span>
                    <XMarkIcon class="h-5 w-5" aria-hidden="true" />
                  </button>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </template>
  
  <script setup>
  
  import { ref } from 'vue'
  import { CheckCircleIcon, XCircleIcon } from '@heroicons/vue/20/solid'
  import { XMarkIcon } from '@heroicons/vue/20/solid' 
  
  const props = defineProps(['show', 'type', 'message', 'messageDetails'])
  const emit = defineEmits(['close'])

  </script>