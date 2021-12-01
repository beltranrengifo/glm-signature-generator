<template>
  <div class="preview app-width app-container" id="signature">
    <meta http-equiv="Content-Type" content="text/html charset=UTF-8" />
    <table
      v-if="person.name"
      border="0"
      cellpadding="0"
      style="table-layout: auto; margin-top: 40px"
    >
      <tbody>
        <tr>
          <td v-if="person.image" style="width: 170px">
            <img
              :src="getLeftImage"
              width="170"
              height="163"
              alt="Grupo La Musa"
              title="Grupo La Musa"
            />
          </td>
          <td style="width: 10px"></td>
          <td :style="getContentColumnStyles">
            <p
              style="
                -webkit-margin-before: 0;
                -webkit-margin-after: 0;
                font-family: Lucida Sans, Arial, sans-serif;
                font-size: 14px;
                color: #473741;
                letter-spacing: 1px;
                margin: 12px 0 0 0;
              "
            >
              <strong>{{ person.name }}</strong>
            </p>
            <p
              v-if="person.role"
              style="
                -webkit-margin-before: 0;
                -webkit-margin-after: 0;
                font-family: Lucida Sans, Arial, sans-serif;
                font-size: 14px;
                color: #473741;
                letter-spacing: 1px;
                margin: 0;
              "
            >
              {{ person.role }}
            </p>
            <a
              v-if="person.email"
              :href="`mailto:${person.email}`"
              style="text-decoration: none; word-break: keep-all"
            >
              <p
                style="
                  -webkit-margin-before: 0;
                  -webkit-margin-after: 0;
                  font-family: Lucida Sans, Arial, sans-serif;
                  font-size: 12px;
                  color: #473741;
                  letter-spacing: 1px;
                  margin: 0;
                  word-break: keep-all;
                  white-space: nowrap;
                "
              >
                {{ person.email }}
              </p>
            </a>
            <a href="https://grupolamusa.com" style="text-decoration: none">
              <p
                style="
                  -webkit-margin-before: 0;
                  -webkit-margin-after: 0;
                  font-family: Lucida Sans, Arial, sans-serif;
                  font-size: 12px;
                  color: #473741;
                  letter-spacing: 1px;
                  margin: 0;
                "
              >
                www.grupolamusa.com
              </p>
            </a>
            <p
              v-if="person.phone"
              style="
                -webkit-margin-before: 0;
                -webkit-margin-after: 0;
                font-family: Lucida Sans, Arial, sans-serif;
                font-size: 12px;
                color: #473741;
                letter-spacing: 1px;
                margin: 0;
              "
            >
              Tfno. {{ person.phone }}
            </p>
            <a
              v-if="person.facebook"
              :href="person.facebook"
              style="text-decoration: none"
            >
              <img
                :src="`${STATIC_IMAGES_URL}/grupo-la-musa-fb.jpg`"
                alt="Facebook"
                width="25"
                height="25"
                style="margin: 5px 0 0 0"
              />
            </a>
            <a
              v-if="person.instagram"
              :href="person.instagram"
              style="text-decoration: none"
            >
              <img
                :src="`${STATIC_IMAGES_URL}/grupo-la-musa-ig.jpg`"
                alt="Instagram"
                width="25"
                height="25"
                style="margin: 5px 0 0 5px"
              />
            </a>
            <a v-if="person.twitter" :href="person.twitter" style="text-decoration: none">
              <img
                :src="`${STATIC_IMAGES_URL}/grupo-la-musa-tw.jpg`"
                alt="Twitter"
                width="25"
                height="25"
                style="margin: 5px 0 0 5px"
              />
            </a>
            <br />
            <a
              v-if="!exceptionallyHideLogoImageFor25Anniversary"
              href="https://grupolamusa.com"
              style="text-decoration: none"
            >
              <img
                :src="getLogoImage"
                alt="Logo Grupo La Musa"
                width="175"
                height="46"
                style="margin: 5px 0 0 0"
              />
            </a>
          </td>
        </tr>
        <tr>
          <td style="height: 25px" colspan="3"></td>
        </tr>
        <tr>
          <td style="vertical-align: top" colspan="3" width="420">
            <p
              style="
                text-align: justify;
                -webkit-margin-before: 0;
                -webkit-margin-after: 0;
                font-size: 7px;
                font-family: Lucida Fax, Georgia, serif;
                font-weight: normal;
                margin: 0;
                color: #473741;
              "
            >
              <strong>AVISO LEGAL</strong>
              : Este mensaje y sus archivos adjuntos van dirigidos exclusivamente a su
              destinatario, pudiendo contener información confidencial sometida a secreto
              profesional. No está permitida su comunicación, reproducción o distribución
              sin la autorización expresa de
              {{ person.company !== 'Otra' ? person.company : person.other }}. Si usted no
              es el destinatario final, por favor elimínelo e infórmenos por esta vía.
            </p>
            <p
              style="
                text-align: justify;
                -webkit-margin-before: 0;
                -webkit-margin-after: 0;
                font-size: 7px;
                font-family: Lucida Fax, Georgia, serif;
                font-weight: normal;
                margin: 6px 0 0;
                color: #473741;
              "
            >
              <strong>PROTECCIÓN DE DATOS</strong>
              : De conformidad con lo dispuesto en el Reglamento (UE) 2016/679, de 27 de
              abril de 2016 (GDPR), y la Ley Orgánica 3/2018, de 5 de diciembre, de
              Protección de Datos Personales y garantía de los derechos digitales
              (LOPDGDD), le informamos que los datos personales y dirección de correo
              electrónico, recabados del propio interesado o de fuentes públicas, serán
              tratados bajo la responsabilidad de
              {{ person.company !== 'Otra' ? person.company : person.other }} para el
              envío de comunicaciones ordinarias vinculadas a nuestros productos y/o
              servicios y se conservarán mientras exista un interés mutuo para ello. Los
              datos no serán comunicados a terceros, salvo obligación legal. Le informamos
              que puede ejercer los derechos de acceso, rectificación, portabilidad y
              supresión de sus datos y los de limitación y oposición a su tratamiento
              dirigiéndose a C/ Manuela Malasaña, 18 - 28004 Madrid (Madrid). Email:
              <a href="maito:protecciondatos@grupolamusa.com">
                protecciondatos@grupolamusa.com
              </a>
              . Si considera que el tratamiento no se ajusta a la normativa vigente, podrá
              presentar una reclamación ante la autoridad de control en
              <a href="www.agpd.es">www.agpd.es</a>
              .
            </p>
          </td>
        </tr>
      </tbody>
    </table>
    <div class="no-signature" v-else>
      <h4>Completa los campos obligatorios</h4>
    </div>
  </div>
</template>

<script>
import { STATIC_IMAGES_URL, IMAGES } from '@/config'

export default {
  name: 'SignaturePrerender',

  props: {
    person: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      STATIC_IMAGES_URL,
      IMAGES,
    }
  },

  computed: {
    exceptionallyHideLogoImageFor25Anniversary() {
      return this.person.useAltLogo
    },

    getLeftImage() {
      return `${STATIC_IMAGES_URL}/${
        this.person.useAltLogo
          ? this.IMAGES.ALTERNATIVE_LEFT_IMAGE
          : this.IMAGES.DEFAULT_LEFT_IMAGE
      }`
    },

    getLogoImage() {
      const images = {
        default: this.IMAGES.DEFAULT_LOGO,
        alt: this.IMAGES.ALTERNATIVE_LOGO,
      }

      const image = this.person.useAltLogo ? 'alt' : 'default'
      try {
        return require(`@/assets/images/${images[image]}`)
      } catch {
        return require(`@/assets/images/${this.DEFAULT_LOGO}`)
      }
    },

    getContentColumnStyles() {
      if (this.exceptionallyHideLogoImageFor25Anniversary) {
        return `
          vertical-align: middle;
        `
      }
      return `
          vertical-align: top;
        `
    },
  },
}
</script>

<style lang="scss" scoped>
.preview {
  min-height: 430px;
  padding: 24px 0 48px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
}
.no-signature {
  font-family: $--font-serif;
  font-style: italic;
  align-self: center;
  h4 {
    font-weight: 100;
    font-size: 14px;
    letter-spacing: 0.5px;
    color: $--color-grey-dark;
  }
}
</style>
