<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-lg-1 d-flex flex-column align-items-start justify-content-between">
        <button class="btn btn-link text-dark text-decoration-none px-0" @click="handleCountry(allData[0])">
          Egypt
        </button>
        <button class="btn btn-link text-dark text-decoration-none px-0" @click="handleCountry(allData[1])">
          USA
        </button>
        <button class="btn btn-link text-dark text-decoration-none px-0" @click="handleCountry(allData[2])">
          London
        </button>
      </div>
      <div class="col-lg-11">

        <GoogleMap api-key="AIzaSyAwcOSQ6hnqoqiXX_1D1ykHOBAZZ2UorHE" style="width: 100%; height: 450px"
          :center="country.locations[0]" :zoom="10"> 
          <Marker v-for="item in country.locations" v-bind:key="item" :options="{ position: item }" />
        </GoogleMap>
      </div>
    </div>

    <div class="mt-4">
      <span> Branches address: {{ country.name }} </span>
      <ul class="list-group">
        <li class="list-group-item" v-for="location in country.locations" v-bind:key="location"> * {{ location.address }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { GoogleMap, Marker } from "vue3-google-map";

export default defineComponent({
  components: { GoogleMap, Marker },
  data() {
    return {
      allData: [
        {
          name: "Egypt",
          detail: "Egypt detail",
          locations: [
            {
              lat: 30.118834,
              lng: 31.349545,
              address: "Heliopolis"
            },
            {
              lat: 30.020940,
              lng: 31.454569,
              address: "New Cairo"
            },
            {
              lat: 30.061838,
              lng: 31.323496,
              address: "Nasr city"
            }
          ]
        },
        {
          name: "USA",
          detail: "USA detail",
          locations: [
            {
              lat: 40.697983,
              lng: -73.776651,
              address: "New York #1"
            },
            {
              lat: 40.877862,
              lng: -74.045816,
              address: "New York #2"
            }
          ]
        },
        {
          name: "London",
          detail: "London detail",
          locations: [
            {
              lat: 51.485820,
              lng: -0.054975,
              address: "London #1"
            },
            {
              lat: 51.525800,
              lng: -0.214637,
              address: "London #2"
            }
          ]
        }
      ],
      country: {
        name: "Egypt",
        detail: "Egypt detail",
        locations: [
          {
            lat: 30.118834,
            lng: 31.349545,
            address: "Heliopolis"
          },
          {
            lat: 30.020940,
            lng: 31.454569,
            address: "New Cairo"
          },
          {
            lat: 30.061838,
            lng: 31.323496,
            address: "Nasr city"
          }
        ]
      },
     
    }
  },
  methods: {
    handleCountry(item) {
      this.country = item
    },
  }
});
</script>