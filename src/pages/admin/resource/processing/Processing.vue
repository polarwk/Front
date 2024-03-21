<script setup lang="ts">
import myStore from "../../../../stores/myStore";
import { useColors, VaCard, VaCardContent } from "vuestic-ui";
import { ref } from "vue";
import { useI18n } from "vue-i18n";

const { t } = useI18n()
const { colors } = useColors();


var EM_fossil = 0;
var EM_elec = 0;
var EM_chemi = 0;
var EM_process = 0;
var EM_recyc = 0;

for (let i = 0; i < myStore.state.consumables_detail.length; i++){
  let type = myStore.state.consumables_detail[i].type.id;
  let name = myStore.state.consumables_detail[i].name.description;
  let unit = myStore.state.consumables_detail[i].unit;
  let consumption = myStore.state.consumables_detail[i].consumption;

  if (type === 1){
    let EF_fossi = myStore.state.EF_fossil[name]
    EM_fossil += consumption * EF_fossi;
  }
  if (type === 2){
    let ProvenceSelected = myStore.state.company.ProvenceSelected.description
    let EF_elec = myStore.state.EF_elec[ProvenceSelected];
    EM_elec += consumption * EF_elec;
  }

  if (type === 3){
    let EF_chemi = myStore.state.EF_chemi[name];
    EM_chemi += consumption * EF_chemi;
  }
}

EM_process = EM_fossil + EM_fossil + EM_chemi;
myStore.state.EM_process = EM_process;

EM_recyc = EM_process + myStore.state.EM_transport

myStore.state.EM_recyc = EM_recyc;




const infoTiles = ref([
  {
    color: 'info',
    value: EM_fossil,
    text: 'sum(EM_fossil)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_elec,
    text: 'sum(EM_elec)',
    icon: '',
  },
  {
    color: 'info',
    value: EM_chemi,
    text: 'sum(EM_chemi)',
    icon: '',
  },
  {
    color: 'success',
    value: EM_process,
    text: 'EM_process',
    icon: '',
  },
  {
    color: 'success',
    value: myStore.state.EM_transport,
    text: 'EM_transport',
    icon: '',
  },
  {
    color: 'success',
    value: EM_recyc,
    text: 'EM_recyc',
    icon: '',
  },
])




</script>


<template>

  <div>
    <div class="col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full pb-6 grid grid-cols-12 gap-6">
        <va-card v-for="(info, idx) in infoTiles" :key="idx" class="col-span-12 sm:col-span-2 mb-8"
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
