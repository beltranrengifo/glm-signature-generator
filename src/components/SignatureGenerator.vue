<template>
  <div class="form__container">
    <div class="form__item required">
      <label class="label" for="name">Nombre</label>
      <input class="input" type="text" id="name" name="name" v-model="signature.name" />
    </div>
    <div class="form__item">
      <label class="label" for="role">Rol</label>
      <input class="input" type="text" id="role" name="role" v-model="signature.role" />
    </div>
    <div class="form__item">
      <label class="label" for="email">Email</label>
      <input
        class="input"
        type="email"
        id="email"
        name="email"
        v-model="signature.email"
      />
    </div>
    <div class="form__item">
      <label class="label" for="phone">Teléfono</label>
      <input
        class="input"
        type="phone"
        id="phone"
        name="phone"
        v-model="signature.phone"
      />
    </div>
    <div class="form__item">
      <label class="label" for="facebook">Facebook URL</label>
      <input
        class="input"
        type="url"
        id="facebook"
        name="facebook"
        v-model="signature.facebook"
      />
    </div>
    <div class="form__item">
      <label class="label" for="instagram">Instagram URL</label>
      <input
        class="input"
        type="url"
        id="instagram"
        name="instagram"
        v-model="signature.instagram"
      />
    </div>
    <div class="form__item">
      <label class="label" for="twitter">Twitter URL</label>
      <input
        class="input"
        type="url"
        id="twitter"
        name="twitter"
        v-model="signature.twitter"
      />
    </div>
    <div class="form__item is-select required">
      <label class="label" for="company">Empresa</label>
      <select
        class="select"
        type="text"
        id="company"
        name="company"
        v-model="signature.company"
      >
        <option v-for="option in companies" :key="option">{{ option }}</option>
      </select>
    </div>
    <div v-if="signature.company === 'Otra'" class="form__item required">
      <label class="label" for="other">Otra empresa</label>
      <input
        class="input"
        type="text"
        id="other"
        name="other"
        v-model="signature.other"
      />
    </div>
    <div class="form__item">
      <label class="label" for="image">Ocultar imagen</label>
      <toggle-button @change="signature.image = !signature.image" />
    </div>
    <div class="form__item">
      <label class="label" for="image">Usar logo del 25 Aniversario</label>
      <toggle-button @change="signature.useAltLogo = !signature.useAltLogo" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'SignatureGenerator',

  data() {
    return {
      signature: {
        name: '',
        role: '',
        email: '',
        phone: '',
        facebook: '',
        instagram: '',
        twitter: '',
        company: '',
        other: '',
        image: true,
        useAltLogo: false,
      },
      companies: [
        'BERODE RESTAURACIÓN, S.L.',
        'BUENALSANTA, S.L.',
        'DESCATALOGADO, S.L.',
        'MUSA LATINA, S.L.',
        'MUSA MALASAÑA, S.L.',
        'PALEO ESPELTO, S.L.',
        'SPIEDO GRILL, S.L.',
        'BRASAS CON PALA S.L.',
        'Otra',
      ],
    }
  },

  watch: {
    signature: {
      deep: true,
      immediate: true,
      handler(val) {
        this.$emit('signatureChange', val)
      },
    },
  },
}
</script>

<style lang="scss" scoped>
.form {
  &__container {
    padding: 32px 16px 0;
    display: flex;
    flex-wrap: wrap;
  }
  &__item {
    width: 50%;
    display: flex;
    flex-direction: column;
    margin-bottom: 42px;
    padding: 0 8px;
    box-sizing: border-box;
    @include phone {
      width: 100%;
    }
    &:last-child {
      margin-bottom: 32px;
    }
  }
}
</style>
