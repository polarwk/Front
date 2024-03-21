<script setup lang="ts">
import myStore from "../../../../stores/myStore";
import { reactive, ref } from "vue";
import { useI18n } from 'vue-i18n'
import { VaCarousel, VaModal, VaCard, VaCardContent, VaCardTitle, VaButton, VaImage, useColors } from 'vuestic-ui'

const { t } = useI18n()
const { colors } = useColors()


const infoTiles = ref([
  {
    color: 'success',
    value: myStore.state.EF_paper,
    text: 'EF_paper',
    icon: '',
  },
  {
    color: 'danger',
    value: myStore.state.EF_pla,
    text: 'EF_pla',
    icon: '',
  },
  {
    color: 'info',
    value: myStore.state.EF_alum,
    text: 'EF_alum',
    icon: '',
  },
])

let Craft = myStore.state.report.craftsmanship.id


const form1 = reactive({
  EF_avoid: 0,
  θ: 0,
});

myStore.state.EM_base1 = myStore.state.report.total * (myStore.state.EF_paper + myStore.state.EF_pla + myStore.state.EF_alum);


function save() {
    myStore.state.EM_base1 = myStore.state.report.total * form1.EF_avoid * form1.θ;
}




</script>

<template>

  <div v-if="Craft === 1">
    <div class="mb-4 grid grid-cols-12 gap-6">
      <va-card class="col-span-12 row justify-space-between">
        <va-card-content>
          <span class="company">已选择的主工艺类型：{{myStore.state.report.craftsmanship.description}}</span>
        </va-card-content>
      </va-card>
    </div>


    <div class="col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full pb-6 grid grid-cols-12 gap-6">
        <va-card v-for="(info, idx) in infoTiles" :key="idx" class="col-span-12 sm:col-span-4 mb-8" :color="info.color">
          <va-card-content>
            <h2 class="va-h2 m-0 text-white">{{ info.value }}</h2>
            <p class="text-white">{{ t(info.text) }}</p>
          </va-card-content>
        </va-card>
      </div>

      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-2">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{ myStore.state.report.total * (myStore.state.EF_paper + myStore.state.EF_pla + myStore.state.EF_alum)}} =  </h2>
            <p class="no-wrap"> EM_base1 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-10">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">weight</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> * ( </h2>
  <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.EF_paper}}</h2>
              <p class="va-text-center">EF_paper</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">+</h2>
  <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.info }">{{myStore.state.EF_pla}}</h2>
              <p class="va-text-center no-wrap">EM_pla</p>
            </div>

            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.info }"> + </h2>
              <!--            <p class="va-text-center no-wrap">EM_pla</p>-->
            </div>

            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.warning }">{{myStore.state.EF_alum}}</h2>
              <p class="va-text-center">EM_alum</p>
            </div>

            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.warning }"> ) </h2>
  <!--            <p class="va-text-center">EM_alum</p>-->
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>
  </div>

  <div v-if="Craft === 2">
    <div class="mb-4 grid grid-cols-12 gap-6">
      <va-card class="col-span-12 row justify-space-between">
        <va-card-content>
          <span class="company">已选择的主工艺类型：{{myStore.state.report.craftsmanship.description}}</span>
        </va-card-content>
      </va-card>
    </div>

    <div class="pb-6 form-elements grid grid-cols-12 gap-6">
      <va-card class="col-span-12">
        <va-card-title>请输入主要再生产品的避免排放因子，并在备注中注明来源</va-card-title>
        <va-card-content>
          <form>
            <div class="grid grid-cols-12 gap-6">
              <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
                <va-input v-model="form1.EF_avoid" placeholder="主要再生产品的避免排放因子" label="EF_avoid" />
              </div>

              <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
                <va-input v-model="form1.θ" placeholder="再生产品在多大程度上能够替代其功能相似的产品,单位为%" label="θ" />
              </div>

              <va-button class="save-button" @click="save">
                <va-icon name="check" />
                保存参数
              </va-button>

            </div>
          </form>
        </va-card-content>
      </va-card>
    </div>



    <div class="col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{ myStore.state.report.total * form1.EF_avoid * form1.θ}} =  </h2>
            <p class="no-wrap"> EM_base1 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">weight</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{form1.EF_avoid}}</h2>
              <p class="va-text-center">EF_avoid</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.info }">{{form1.θ}}</h2>
              <p class="va-text-center no-wrap">θ</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>

  </div>

</template>

<style scoped lang="scss">

.company {
  margin-top: 20px;
  font-size: 1.5rem;
  font-weight: bolder;
}

</style>
