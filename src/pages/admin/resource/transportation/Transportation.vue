<script setup lang="ts">
import myStore from "../../../../stores/myStore";
import { useColors, VaCard, VaCardContent } from "vuestic-ui";
import { ref } from "vue";
import { useI18n } from "vue-i18n";

const { t } = useI18n()
const { colors } = useColors();





const calculationMethodId = myStore.state.trans.calculation.id;
const calculationMethod = myStore.state.trans.calculation.description;

console.log(calculationMethodId)

var EM_co2 = 0;
var EM_ch4 = 0;
var EM_n2o = 0;
var EM_transport = 0;

if (calculationMethodId === 1) {
  for (let i = 0; i < myStore.state.trans_detail.length; i++) {
    let carType = myStore.state.trans_detail[i].trans.description;
    let fuelType = myStore.state.trans_detail[i].fuel.description;
    let volume = myStore.state.trans_detail[i].volume;
    let times = myStore.state.trans_detail[i].times;
    let mileage = myStore.state.trans_detail[i].mileage;
    let EF_co2 = myStore.state.EF_co2[fuelType];
    EM_co2 += volume * mileage * times;


    let EF_ch4 = myStore.state.EF_ch4[carType][fuelType];
    let EF_n2o = myStore.state.EF_n2o[carType][fuelType];

    EM_ch4 += mileage * times * EF_ch4;
    EM_n2o += mileage * times * EF_n2o;
  }
  EM_transport = EM_co2 + EM_ch4 + EM_n2o;
}


if (calculationMethodId === 2) {
  for (let i = 0; i < myStore.state.trans_detail.length; i++) {
    let carType = myStore.state.trans_detail[i].trans.description;
    let fuelType = myStore.state.trans_detail[i].fuel.description;
    let times = myStore.state.trans_detail[i].times;
    let mileage = myStore.state.trans_detail[i].mileage;
    let weight = myStore.state.trans_detail[i].weight;
    let unitEnergy = myStore.state.unitEnergyConsume[fuelType];
    let EF_co2 = myStore.state.EF_co2[fuelType];
    EM_co2 += mileage * weight * times * EF_co2 * unitEnergy;


    let EF_ch4 = myStore.state.EF_ch4[carType][fuelType];
    let EF_n2o = myStore.state.EF_n2o[carType][fuelType];

    EM_ch4 += mileage * times * EF_ch4;
    EM_n2o += mileage * times * EF_n2o;
  }
  EM_transport = EM_co2 + EM_ch4 + EM_n2o;
}


if (calculationMethodId === 3) {
  for (let i = 0; i < myStore.state.trans_detail.length; i++) {
    let carType = myStore.state.trans_detail[i].trans.description;
    let fuelType = myStore.state.trans_detail[i].fuel.description;
    let times = myStore.state.trans_detail[i].times;
    let mileage = myStore.state.trans_detail[i].mileage;
    let fuelPer = myStore.state.trans_detail[i].fuelPer;

    let EF_co2 = myStore.state.EF_co2[fuelType];
    EM_co2 += mileage * fuelPer * times * EF_co2;


    let EF_ch4 = myStore.state.EF_ch4[carType][fuelType];
    let EF_n2o = myStore.state.EF_n2o[carType][fuelType];

    EM_ch4 += mileage * times * EF_ch4;
    EM_n2o += mileage * times * EF_n2o;
  }
  EM_transport = EM_co2 + EM_ch4 + EM_n2o;
  myStore.state.EM_transport = EM_transport
}


const   infoTiles = ref([
  {
    color: 'info',
    value: EM_co2,
    text: 'sum(EM_co2)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_ch4,
    text: 'sum(EM_ch4)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_n2o,
    text: 'sum(EM_n2o)',
    icon: '',
  },
  {
    color: 'success',
    value: EM_transport,
    text: 'EM_transport',
    icon: '',
  },
])




</script>


<template>

  <div>
    <div class="mb-4 grid grid-cols-12 gap-6">
      <va-card class="col-span-12 row justify-space-between">
        <va-card-content>
          <span class="company">已选择的计算方式：{{ calculationMethod }}</span>
        </va-card-content>
      </va-card>
    </div>

    <div class="col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full pb-6 grid grid-cols-12 gap-6">
        <va-card v-for="(info, idx) in infoTiles" :key="idx" class="col-span-12 sm:col-span-3 mb-8"
                 :color="info.color">
          <va-card-content>
            <h2 class="va-h2 m-0 text-white">{{ info.value }}</h2>
            <p class="text-white">{{ t(info.text) }}</p>
          </va-card-content>
        </va-card>
      </div>
    </div>
  </div>


</template>

<style scoped lang="scss">

</style>
