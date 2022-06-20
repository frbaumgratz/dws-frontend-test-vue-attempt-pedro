<template>
  <ul id="result" class="user-list max-h-5">
    <li class="flex p-5" v-for="band in filteredBands" :key="band.name">
      <img
        class="h-12 w-12 object-contain rounded-full"
        :src="band.image"
        alt="band_img"
      />
      <div class="ml-3">
        <h4 class="font-semibold text-gray-600">{{ band.name }}</h4>
        <p class="font-light text-gray-500 text-sm -mt-1">
          {{ band.numPlays }} {{ calculatePlays(band.numPlays) }}
        </p>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  mounted() {
    this.getData();
    //  this.filterByName();
  },
  methods: {
    async getData() {
      const res = await fetch(
        "https://iws-brazil-labs-iws-recruiting-bands.iwsbrazil.io/api/bands"
      );

      const data = await res.json();

      this.bands = data;
      this.filterByName();
    },

    calculatePlays(numPlays) {
      if (numPlays > 4471468) {
        return "plays";
      } else {
        return "playzinhos";
      }
    },

    filterByName() {
      console.log(this.bands);
      const result = this.bands.filter(filterData);
      function filterData(band) {
        return band.name.includes("on");
      }
      this.filteredBands = result;
      console.log("123");
    },
  },
  data() {
    return {
      bands: [],
      filteredBands: [],
    };
  },
};
</script>

<style lang="scss" scoped></style>
