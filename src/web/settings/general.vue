<template>
  <div class="max-w-md p-2">
    <div class="mb-2">
      <div class="flex-1 mb-1">{{ $t('Font size') }} <span class="bg-gray-200 text-gray-900 rounded px-1">{{ $t('Restart required') }}</span></div>
      <div class="mb-4 flex">
        <input v-model.number="config.fontSize" class="rounded bg-gray-900 px-1 block w-16 mb-1 font-fontin-regular text-center" />
        <span class="ml-1">px</span>
      </div>
    </div>
    <div class="mb-2">
      <div class="flex-1 mb-1">{{ $t('Clicking on background focuses game') }}</div>
      <div class="mb-4 flex">
        <ui-radio v-model="config.overlayBackgroundClose" :value="false" class="mr-4">{{ $t('No') }}</ui-radio>
        <ui-radio v-model="config.overlayBackgroundClose" :value="true" class="mr-4">{{ $t('Yes') }}</ui-radio>
      </div>
    </div>
    <div class="mb-2">
      <div class="flex-1 mb-1">{{ $t('Background, when APT window is clickable') }}</div>
      <div class="mb-1 flex">
        <input v-model="config.overlayBackground" class="rounded bg-gray-900 px-1 block w-48 mb-1 mr-4 font-fontin-regular text-center" />
        <ui-radio v-model="config.overlayBackground" value="rgba(255, 255, 255, 0)">{{ $t('Transparent') }}</ui-radio>
      </div>
      <div class="mb-4" v-if="config.overlayBackground !== 'rgba(255, 255, 255, 0)'">
        <ui-radio v-model="config.overlayBackgroundExclusive" :value="true" class="mr-4">{{ $t('Show for Overlay and Price Check') }}</ui-radio><br>
        <ui-radio v-model="config.overlayBackgroundExclusive" :value="false">{{ $t('Show only for Overlay') }}</ui-radio>
      </div>
    </div>
    <div class="mb-2">
      <div class="flex-1 mb-1">{{ $t('Language') }} <span class="bg-gray-200 text-gray-900 rounded px-1">{{ $t('Restart required') }}</span></div>
      <div class="mb-4 flex">
        <ui-radio v-model="config.language" value="en" class="mr-4">English</ui-radio>
        <ui-radio v-model="config.language" value="ru" class="mr-4">Русский</ui-radio>
      </div>
    </div>
  </div>
</template>

<script>
import { Config } from '@/web/Config'

export default {
  computed: {
    config () {
      return Config.store
    }
  }
}
</script>

<i18n>
{
  "ru": {
    "Font size": "Размер шрифта",
    "Background, when APT window is clickable": "Фон, когда окно APT кликабельно",
    "Transparent": "Прозрачный",
    "Show for Overlay and Price Check": "Показывать для оверлея и прайс-чека",
    "Show only for Overlay": "Показывать только для оверлея",
    "Clicking on background focuses game": "Нажатие по фону активирует окно игры",
    "Language": "Язык"
  }
}
</i18n>
