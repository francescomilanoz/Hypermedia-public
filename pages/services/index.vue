<template>
  <div id="app-container">
    <Cover
      title="Services"
      preview-text="Solve your business problems with Hypermood services. Please feel free to take a look and explore as much as you like."
      thumbnail="https://static.wixstatic.com/media/357df1_02076c63bb6646aca086fd34f7f60292~mv2.jpg"
    />
    <h1 class="blue-title">All our services, divided by areas</h1>
    <div v-for="area in areas" :key="area.id">
      <AreaName :id="area.id" :name="area.name" :logo="area.image" />
      <ServicesPreviewList :services="area.services" />
    </div>
  </div>
</template>

<script>
import Cover from '~/components/Cover'
import AreaName from '~/components/Areas/AreaName'
import ServicesPreviewList from '~/components/Services/ServicesPreviewList'
export default {
  components: {
    Cover,
    AreaName,
    ServicesPreviewList,
  },
  async asyncData({ $axios, route }) {
    const { data } = await $axios.get(
      `${process.env.BASE_URL}/api/areaservices`
    )
    const areas = data
    return {
      areas,
    }
  },
  head() {
    return {
      title: 'Services - Hypermood',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Click here to find out more about Hypermood services!',
        },
      ],
    }
  },
}
</script>

<style scoped>
#app-container {
  padding-bottom: 80px;
}
h1 {
  margin-top: -20px;
  margin-left: 10%;
  margin-right: 10%;
  text-align: center;
}
@media (max-width: 350px) {
  h1 {
    font-size: 25px;
  }
}
</style>
