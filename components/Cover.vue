<template>
  <div id="container">
    <div id="patina"></div>
    <div
      id="bar-container"
      :style="{ backgroundImage: 'url(' + thumbnail + ')' }"
    ></div>
    <div id="bar-content">
      <OrientationInfo
        v-if="!(parentSectionText === '/')"
        id="orientation-info"
        :text="parentSectionText"
        :section-name="parentSectionName"
      />
      <h1>{{ title }}</h1>
      <p>{{ previewText }}</p>
    </div>
  </div>
</template>

<script>
import OrientationInfo from '~/components/navigation/OrientationInfo'
export default {
  name: 'Cover',
  components: {
    OrientationInfo,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    previewText: {
      type: String,
      required: true,
    },
    thumbnail: {
      type: String,
      required: true,
    },
    parentSectionText: {
      type: String,
      required: false,
      default: '/',
    },
    parentSectionName: {
      type: String,
      required: false,
      default: '',
    },
  },
}
</script>

<style scoped>
#container {
  width: 100%;
  height: 400px;
  position: relative;
  background-position: center;
  background-size: cover;
  padding: 0px;
  top: -60px; /* Same size as header - It makes it go under it from the beginning */
}

#bar-container {
  width: 100%;
  height: 400px;
  position: relative;
  background-position: center;
  background-size: cover;
  z-index: -1;
}
#patina {
  width: 100%;
  height: 400px;
  position: absolute;
  top: 0;
  left: 0;
  background-color: black;
  opacity: 0.6;
  z-index: +1;
}

#bar-content {
  max-width: 550px;
  position: absolute;
  top: 0;
  left: 0;
  padding-left: 10%;
  padding-top: 100px;
  text-align: left;
  color: white;
  z-index: +2;
}

#orientation-info {
  margin-left: -10%;
}

@media (max-width: 630px) {
  #bar-content {
    width: 350px;
  }
}
@media (max-width: 400px) {
  #bar-content {
    width: 230px;
  }
}
@media (max-width: 350px) {
  h1 {
    font-size: 25px;
  }
}
</style>
