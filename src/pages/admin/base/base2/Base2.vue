<script setup lang="ts">

import myStore from "../../../../stores/myStore";
import { useColors, VaCard, VaCardContent } from "vuestic-ui";


const { colors } = useColors()

const D_base = myStore.state.report.total / (myStore.state.m * myStore.state.D_T)


</script>

<template>

  <div>
    <div class="mb-4 grid grid-cols-12 gap-6">
      <va-card class="col-span-12 row justify-space-between">
        <va-card-content>
          <span class="company">焚烧阶段</span>
        </va-card-content>
      </va-card>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{ myStore.state.report.total / (myStore.state.m * myStore.state.D_T)}} =  </h2>
            <p class="no-wrap"> D_base </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">weight</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> / ( </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">m</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.info }">{{myStore.state.D_T}}</h2>
              <p class="va-text-center no-wrap">D_T</p>
            </div>

            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> ) </h2>
              <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>



    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_co2 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">百公里油耗</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.info }">{{myStore.state.D_T}}</h2>
              <p class="va-text-center no-wrap">EF_co2</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_ch4 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EF_ch4</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_n2o </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EF_n2o</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_transport </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">0.066325</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_co2 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">百公里油耗</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">EF_paper</p>-->
            </div>

            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.info }">{{myStore.state.D_T}}</h2>
              <p class="va-text-center no-wrap">EF_co2</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_ch4 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EF_ch4</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_n2o </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> *  </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EF_n2o</p>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_process </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_co2</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EM_ch4</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EM_n2o</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h2 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_incineration </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_transport</p>
            </div>
            <div class="col-span-1 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-4 flex flex-col">
              <h2 class="va-h2 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.m}}</h2>
              <p class="va-text-center">EM_process</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 grid grid-cols-12 gap-6">
      <va-card class="col-span-12 row justify-space-between">
        <va-card-content>
          <span class="company">填埋阶段</span>
        </va-card-content>
      </va-card>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_transport </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">D_base</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">0.066325</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_ch4 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">回收总量</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> * </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">EF_ch4</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>

    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_process </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_ch4</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_landfill </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_transport</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">EF_process</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>



    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_base2 </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_incineration</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">EF_landfill</p>
            </div>

          </va-card-content>
        </va-card>
      </div>
    </div>


    <div class="mb-4 col-span-12 lg:col-span-6 flex flex-wrap">
      <div class="w-full grid grid-cols-12 gap-6">
        <va-card class="col-span-12 sm:col-span-4">
          <va-card-content class="h-full flex flex-col justify-center">
            <h2 class="va-h6 m-0" :style="{ color: colors.primary }"> {{666}} =  </h2>
            <p class="no-wrap"> EM_base </p>
          </va-card-content>
        </va-card>
        <va-card class="col-span-12 sm:col-span-8">
          <va-card-content class="grid grid-cols-12 row-separated">
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">{{myStore.state.report.total}}</h2>
              <p class="va-text-center">EM_base1</p>
            </div>
            <div class="col-span-1 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }"> + </h2>
              <!--            <p class="va-text-center">weight</p>-->
            </div>
            <div class="col-span-2 p-0 flex flex-col">
              <h2 class="va-h6 m-0 va-text-center" :style="{ color: colors.primary }">0.066325</h2>
              <p class="va-text-center">EF_base2</p>
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
