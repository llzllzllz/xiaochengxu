<template>
  <div style="width:100%;height: 100%;">
   <map
      id="map"
      longitude="114.336"
      latitude="30.5838"
      scale="16"
      :controls="controls"
      @controltap="controltap($event)"
      :markers="markers"
      @markertap="markertap($event)"
      :polyline="polyline"
      @regionchange="regionchange($event)"
      show-location
      style="width: 100%; height: 100%;"
  ></map>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      markers: [{
        iconPath: '/static/images/marker.png',
        id: 0,
        latitude: 30.5838,
        longitude: 114.336,
        width: 50,
        height: 50
      }],
      polyline: [{
        points: [{
        longitude: 114.336,
        latitude: 30.5838
      }, {
        longitude: 114.341175,
        latitude: 30.584859
      }],
      color: '#FF0000DD',
      width: 2,
      dottedLine: true
    }],
    controls: [{
      id: 1,
      iconPath: '/static/images/location.png',
      position: {
        left: 0,
        top: 300 - 50,
        width: 50,
        height: 50
      },
      clickable: true
    }]
    }
  },

  methods: {
  regionchange(event) {
    console.log(event)
  },
  markertap(event) {
    console.log(event)
  },
  controltap(event) {
    console.log(event)
  }
  },

  created () {
  }
}
</script>

<style>
body,html{height:100%}
</style>
