<script lang="ts">
export default {
  name: "App",
  layoutName:'default',
}
</script>
<script setup lang="ts">

import { computed } from 'vue'
import { useMagicKeys } from '@vueuse/core';
import Key from '/@/components/Key.vue';
import { useDark,useToggle } from '@vueuse/core'
const { shift, t, e, z, u, s, t_e_z, u_s_e, current } = useMagicKeys()
const keys = computed(() => Array.from(current))


const isDark = useDark({
  selector: 'body',
  attribute: 'class',
  valueDark: 'dark',
  valueLight: 'light',
  });

const toggleDark = useToggle(isDark)
</script>

<template>
<div>
  <div class="grid justify-items-end max-w-7xl" style="margin:20px">


    <label for="checked-toggle" class="inline-flex relative items-center cursor-pointer">
      <input @click="toggleDark()" type="checkbox" :value="isDark" id="checked-toggle" class="sr-only peer" checked>
      <div class="w-11 h-6 bg-gray-200 rounded-full peer peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-800 dark:bg-gray-700 peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-0.5 after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
        <span class="ml-3 text-sm font-medium light:text-gray-900 dark:text-sky-50">{{ isDark ? 'Dark' : 'Light' }}</span>
    </label>

  </div>
  <div class="flex flex-col md:flex-row max-w-7xl mx-auto dark:bg-slate-800 dark:text-white " style="margin: 50px  100px">
    <img
      src="/favicon.ico"
      class="h-38 py-8 m-auto transform transistion duration-500"
      :class="{ 'opacity-0': !t_e_z, 'rotate-180': shift }"
    >

    <div>
      <note class="text-center mt-0 mb-5">
        Press the following keys togehter  to test out
      </note>
      <div class="flex gap-3 justify-center mt-5">
        <Key :value="t">
          T
        </Key>
        <Key :value="e">
          e
        </Key>
        <Key :value="z">
          z
        </Key>

      </div>

      <div class="flex gap-3 justify-center mt-3">
        <Key :value="shift">
          Shift
        </Key>
        <Key :value="t_e_z">
          Tez
        </Key>

      </div>

      <div class="text-center mt-4">
        <Note>Keys Pressed</Note>
        <div class="flex mt-2 justify-center space-x-1 min-h-1.5em">
          <code
            v-for="key in keys"
            :key="key"
          >
            {{ key }}
          </code>
        </div>
      </div>
    </div>

  
  </div>

  </div>
</template>

<style >
body.dark{
  background-color: black;
  color: white;
  
}
body.light{
  background-color: white;
  color: black;
  
}
</style>