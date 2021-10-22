<template>
  <div id="app">
    <header id="main-header">
      <logo :logo="logo" alt="Grupo La Musa" />
      <title-component title="Generador de firmas" tag="h1" />
    </header>
    <section>
      <title-component class="app-width preview-header" title="Instrucciones" />
      <div class="app-container app-width">
        <instructions-block type="Mail OSX" :content="instructions.mail" />
        <instructions-block type="Mail iOS" :content="instructions.ios" />
        <instructions-block type="Outlook" :content="instructions.outlook" />
        <instructions-block type="Gmail" :content="instructions.gmail" />
      </div>
    </section>
    <section class="m-t-48">
      <title-component class="app-width" title="Crea tu firma" tag="h2" />
      <div class="app-container app-width">
        <signature-generator @signatureChange="updateSignature" />
      </div>
    </section>
    <section class="m-t-48">
      <header class="app-width preview-header">
        <title-component title="Vista previa" />
        <copy-button
          :class="{ disabled: !person.name || !person.company }"
          elementToCopy="#signature"
        />
      </header>
      <signature-prerender :person="person" />
    </section>
  </div>
</template>

<script>
import { IMAGES } from '@/config'
import SignatureGenerator from '@/components/SignatureGenerator.vue'
import TitleComponent from '@/components/TitleComponent.vue'
import Logo from '@/components/Logo.vue'
import SignaturePrerender from '@/components/SignaturePrerender.vue'
import CopyButton from '@/components/CopyButton.vue'
import InstructionsBlock from '@/components/InstructionsBlock.vue'
import instructions from '@/assets/js/instructions'

export default {
  name: 'app',

  components: {
    SignatureGenerator,
    TitleComponent,
    Logo,
    SignaturePrerender,
    CopyButton,
    InstructionsBlock,
  },

  data() {
    return {
      subtitle: 'Grupo La Musa',
      person: {},
      copyButtonText: 'Copiar',
      instructions: instructions,
      IMAGES,
    }
  },

  computed: {
    logo() {
      return require(`@/assets/images/${this.IMAGES.DEFAULT_LOGO}`)
    },
  },

  methods: {
    updateSignature(val) {
      this.person = val
    },
  },
}
</script>

<style lang="scss" scoped>
#app {
  background: $--color-grey;
  min-height: 100vh;
  padding: 0 48px 48px;
  box-sizing: border-box;
}
.app-width {
  width: 800px;
  max-width: 100%;
  margin: 0 auto;
}
.app-container {
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.05);
  background: $--color-white;
  border-radius: 4px;
}
.preview-header {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}
#main-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  /deep/ h1 {
    font-size: 16px;
  }
}
</style>
