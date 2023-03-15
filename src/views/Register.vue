<template>
  <div class="container">
    <div class="head">
      <h3>Register Now!</h3>
    </div>
    <div class="form">
      <div class="field">
        <label for="name">Full Name</label>
        <input id="name" type="text" v-model="name">
      </div>
      <div class="field">
        <label for="company">Company</label>
        <input id="company" type="text" v-model="company">
      </div>
      <div class="field">
        <label for="country">Country</label>
        <select id="country" v-model="selectedCountry">
          <option v-for="cnt in country" :key="cnt.countryCode" :value="cnt">
            {{ cnt.countryName }}
          </option>
        </select>
      </div>
      <div class="field">
        <label for="city">City</label>
        <select id="city" v-model="selectedCity">
          <option v-for="ct in cityFiltered" :key="ct.cityCode" :value="ct">
            {{ ct.cityName }}
          </option>
        </select>
      </div>
    </div>
    <button @click="submit">Submit</button>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';

const country = ref([
  {
    countryName: "Malaysia",
    countryCode: "MYS"
  },
  {
    countryName: "Singapore",
    countryCode: "SIN"
  },
  {
    countryName: "Indonesia",
    countryCode: "IDN"
  },
  {
    countryName: "India",
    countryCode: "NDI"
  }
]);

const city = ref([
  {
    cityName: "Kuala Lumpur",
    cityCode: "KLU",
    countryCode: "MYS"
  },
  {
    cityName: "Jaipur",
    cityCode: "JIP",
    countryCode: "NDI"
  },
  {
    cityName: "Jakarta",
    cityCode: "JKT",
    countryCode: "IDN"
  },
  {
    cityName: "Penang",
    cityCode: "PEN",
    countryCode: "MYS"
  },
  {
    cityName: "Bandung",
    cityCode: "BDO",
    countryCode: "IDN"
  }
]);

const selectedCountry = ref({});
const selectedCity = ref({});
const name = ref('');
const company = ref(''); 

const cityFiltered = computed(() => {
  if (selectedCountry.value.countryCode) {
    const temp = city.value.filter((cty) => cty.countryCode === selectedCountry.value.countryCode)
    console.log(temp);
    return city.value.filter((cty) => cty.countryCode === selectedCountry.value.countryCode)
  }
});

onMounted(() => {
  sortCountry();
})



function sortCountry() {
  console.log('call');
  country.value = country.value.sort((a,b) => a.countryName - b.countryName);
}

function submit() {
  alert(`Name: ${name.value} Company: ${company.value} Country: ${selectedCountry.value.countryCode} City: ${selectedCity.value.cityCode}`)
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  width: 100vw;
  justify-content: center;
  align-items: center;
  margin-top: 100px;
}

.head {
  display: flex;
  justify-content: center;
  align-items: center;
}

.form {
  display: flex;
  align-items: center;
  width: 50vw;
  flex-wrap: wrap;
  margin-bottom: 20px;
}

.field {
  display: flex;
  flex-direction: column;
  width: 20vw;
  margin: 0px 5px;
}

</style>