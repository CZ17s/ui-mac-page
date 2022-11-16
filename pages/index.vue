<template lang="pug">

v-row.mx-start
  v-col.mt-10(cols='12')
    .text-h1.font-weight-regular {{showTime}}
    .text-subtitle-1.font-weight-medium {{showDate}}

  v-row
    v-col.mt-10.text-center(cols='6' sm="6" md="2" v-for="(item, i) in cardIcon" :key="i")
      v-card.ma-3.rounded-xl(:color="item.color" :elevation="10" width="100px" height="100px")
        v-icon.mt-6(color="white" size="56" ) {{item.icon}}
        .text-subtitle-1.font-weight-bold.mt-7 {{item.title}}

  v-col.mt-10(cols='12')
    .text-h6.font-weight-bold Hi Alex!
    .text-h6.font-weight-light No upcoming meetings today



</template>

<script>
import { DateTime } from 'luxon';
export default {
  name: 'IndexPage',
  data() {
    return {
      showTime: "",
      showDate: "",
      showLuxon: "",
      cardIcon: [
      {
        icon: 'mdi-video',
        title: 'Meething',
        color: 'orange'
      },
      {
        icon: 'mdi-plus-box',
        title: 'Join',
        color: 'blue'
      },
      {
        icon: 'mdi-calendar-month-outline',
        title: 'Shedule',
        color: 'blue'
      },
      {
        icon: 'mdi-arrow-up-box',
        title: 'Share Screen',
        color: 'blue'
      }
    ]
    }
  },
  created() {
    setInterval(this.getTime, 1000);
  },
  methods: {
    getTime() {

      const today = new Date();
      const time = today.getHours() + " : " + today.getMinutes() ;
      
      this.showTime = time
      this.showDate = DateTime.now().toLocaleString(DateTime.DATE_MED)

      return this.showTime, this.showDate;

    }
  }
}
</script>

<style scoped>

</style>
