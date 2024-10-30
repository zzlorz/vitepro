<script setup lang="ts">
import { SRGBColorSpace } from 'three';
import { ref } from 'vue';
import { Color } from 'three';

import { useRenderLoop, TresCanvas } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';

import TheModel from './model.vue';

</script>

<template>
  <div style="width: 300px;height: 300px;">
    <Suspense>
      <TresCanvas
        clear-color="#82DBC5"
        shadows
        alpha
        power-preference="high-performance"
        :output-color-space="SRGBColorSpace"
      >
        <TresPerspectiveCamera
          :position="[1, 1, 1]"
          :fov="50"
          :near="0.5"
          :far="1000"
        />
        <OrbitControls />
        <TresAmbientLight :color="0xffffff" :intensity="0.25" />
        <TresDirectionalLight :position="[0, 8, 4]" :intensity="2" cast-shadow />
        <Suspense>
          <TheModel />
        </Suspense>
      </TresCanvas>
    </Suspense>
  </div>
</template>
