<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <br/>
    <template #heading>Сканирование билета</template>
    <qrcode-stream @detect="onDetect"></qrcode-stream>
    <br/>
    <n-button strong secondary type="primary">
      проверить
    </n-button>
  </WelcomeItem>
</template>


<script lang="ts">
import { defineComponent, ref, onMounted, reactive } from 'vue'
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
import { QrcodeStream, QrcodeDropZone, QrcodeCapture } from 'vue-qrcode-reader'

export default {
    components: { QrcodeStream, QrcodeDropZone, QrcodeCapture },
    setup() {
      const readersNumber = ref(0)
      const book = reactive({ title: 'Руководство по Vue 3' })

      //
      const onDetect = (detectedCodes) => {
        console.log(detectedCodes)
      }
      // объявление для шаблона
      return {
        readersNumber,
        book
      }
    }
}
</script>