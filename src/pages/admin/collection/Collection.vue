<script setup lang="ts">
import myStore from "../../../stores/myStore";
import { ref, watch } from "vue";
import { useI18n } from "vue-i18n";
import { reactive } from "vue";

const { t } = useI18n();

const form1 = reactive({
  Name: "",
  code: "",
  ProvenceSelected: "",
  telephone: "",
  email: "",
  address: ""
});

const form2 = reactive({
  reportYear: "",
  craftsmanship: "",
  total: ""
});

const form3 = reactive({
  calculation: { id: 1, description: "基本能耗统计法" }

});

const consumablesType = ref([
  { id: 1, description: "化石燃料" },
  { id: 2, description: "电力" },
  { id: 3, description: "辅料" }
]);

const consumablesName = ref({
  1: [
    { id: 1, description: "无烟煤" },
    { id: 2, description: "烟煤" },
    { id: 3, description: "褐煤" },
    { id: 4, description: "洗精煤" },
    { id: 5, description: "其他洗煤" },
    { id: 6, description: "煤制品" },
    { id: 7, description: "焦炭" },
    { id: 8, description: "原油" },
    { id: 9, description: "燃料油" },
    { id: 10, description: "汽油" },
    { id: 11, description: "柴油" },
    { id: 12, description: "一般煤油" },
    { id: 13, description: "石油焦" },
    { id: 14, description: "其它石油制品" },
    { id: 15, description: "焦油" },
    { id: 16, description: "粗苯" },
    { id: 17, description: "炼厂干气" },
    { id: 18, description: "液化石油气" },
    { id: 19, description: "液化天然气" },
    { id: 20, description: "天然气" },
    { id: 21, description: "焦炉煤气" },
    { id: 22, description: "高炉煤气" },
    { id: 23, description: "转炉煤气" },
    { id: 24, description: "密闭电石炉炉气" }
  ],
  2: [
    { id: 1, description: "外购电力" }
  ],
  3: [
    { id: 1, description: "氢氧化钠(50%)" },
    { id: 2, description: "氢氧化钠(100%)" },
    { id: 3, description: "其他药剂" }
  ]
});



const consumablesUnit = ref({
  1: [
    {id: 1, description: "t"},
    {id: 2, description: "万 Nm3"},
  ],
  2: [
    {id: 1, description: "MWh"},
  ],
  3: [
    {id: 1, description: "t"}
  ]
})



// 基本能耗统计法
const basicFormRows = ref([
  { start: "", end: "", trans: "", fuel: "", volume: "", mileage: "", times: "" } // 初始化一个空行
]);

// 单位周转量能耗统计法
const unitEnergyFormRows = ref([
  { start: "", end: "", trans: "", fuel: "", mileage: "", weight: "", times: "" } // 初始化一个空行
]);


// 单位周转量能耗统计法
const unitMileageFormRows = ref([
  { start: "", end: "", trans: "", fuel: "", mileage: "", times: "", fuelPer: "", resource: "" } // 初始化一个空行
]);

// 消耗品信息表格
const consumablesFormRows = ref([
  { type: "", name: "", unit: "", consumption: "" } // 初始化一个空行
]);


const ProvenceOptions = ref([
  {
    id: 1,
    description: "北京"
  },
  {
    id: 2,
    description: "天津"
  },
  {
    id: 3,
    description: "河北"
  },
  {
    id: 4,
    description: "山西"
  },
  {
    id: 5,
    description: "内蒙古"
  },
  {
    id: 6,
    description: "山东"
  },
  {
    id: 7,
    description: "辽宁"
  },
  {
    id: 8,
    description: "吉林"
  },
  {
    id: 9,
    description: "吉林"
  },
  {
    id: 10,
    description: "黑龙江"
  },
  {
    id: 11,
    description: "上海"
  },
  {
    id: 12,
    description: "江苏"
  },
  {
    id: 13,
    description: "浙江"
  },
  {
    id: 14,
    description: "安徽"
  },
  {
    id: 15,
    description: "河南"
  },
  {
    id: 16,
    description: "湖北"
  },
  {
    id: 17,
    description: "湖南"
  },
  {
    id: 18,
    description: "重庆"
  },
  {
    id: 19,
    description: "四川"
  },
  {
    id: 20,
    description: "广东"
  },
  {
    id: 21,
    description: "广西"
  },
  {
    id: 22,
    description: "贵州"
  },
  {
    id: 23,
    description: "云南"
  },
  {
    id: 24,
    description: "海南"
  },
  {
    id: 25,
    description: "陕西"
  },
  {
    id: 26,
    description: "甘肃"
  },
  {
    id: 27,
    description: "青海"
  },
  {
    id: 28,
    description: "宁夏"
  },
  {
    id: 29,
    description: "新疆"
  }
]);

const YearOptions = ref([
  {
    id: 1,
    description: "2018年"
  },
  {
    id: 2,
    description: "2019年"
  },
  {
    id: 3,
    description: "2020年"
  },
  {
    id: 4,
    description: "2021年"
  },
  {
    id: 5,
    description: "2022年"
  },
  {
    id: 6,
    description: "2023年"
  },
  {
    id: 7,
    description: "2024年"
  }
]);

const CraftOptions = ref([
  {
    id: 1,
    description: "分离式工艺"
  },
  {
    id: 2,
    description: "一体式加工"
  }
]);

const CalculationOptions = ref([
  {
    id: 1,
    description: "基本能耗统计法"
  },
  {
    id: 2,
    description: "单位周转量能耗统计法"
  },
  {
    id: 3,
    description: "单位行驶里程能耗统计法"
  }
]);

const transMethod = ref([
  {
    id: 1,
    description: "重型货车"
  },
  {
    id: 2,
    description: "轻型货车"
  },
  {
    id: 3,
    description: "其他"
  }
]);

const fuelType = ref([
  {
    id: 1,
    description: "汽油"
  },
  {
    id: 2,
    description: "柴油"
  },
  {
    id: 3,
    description: "液化天然气"
  }
]);



function saveCompany() {
  myStore.state.company = form1;
  myStore.state.report = form2;
  myStore.state.trans = form3;
  if (form3.calculation.id === 1) {
    myStore.state.trans_detail = basicFormRows;
  }
  if (form3.calculation.id === 2) {
    myStore.state.trans_detail = unitEnergyFormRows;
  }
  if (form3.calculation.id === 3) {
    myStore.state.trans_detail = unitMileageFormRows;
  }

  myStore.state.consumables_detail = consumablesFormRows;

  // console.log(form3.calculation.id)
}

// 添加新行
function basicFormAddRow() {
  basicFormRows.value.push({ start: "", end: "", trans: "", fuel: "", volume: "", mileage: "", time: "" });
}

// 移除行
function basicFromRemoveRow(rowIndex) {
  basicFormRows.value.splice(rowIndex, 1);
}

// 添加新行
function unitEnergyFormAddRow() {
  unitEnergyFormRows.value.push({ start: "", end: "", trans: "", fuel: "", mileage: "", weight: "", times: "" });
}

// 移除行
function unitEnergyFormRemoveRow(rowIndex) {
  unitEnergyFormRows.value.splice(rowIndex, 1);
}

// 添加新行
function unitMileageFormAddRow() {
  unitMileageFormRows.value.push({ start: "", end: "", trans: "", fuel: "", mileage: "", weight: "", times: "" });
}

// 移除行
function unitMileageFormRemoveRow(rowIndex) {
  unitMileageFormRows.value.splice(rowIndex, 1);
}

function consumablesFormRowsAddRow() {
  consumablesFormRows.value.push({ type: "", name: "", unit: "", consumption: "" });
}

function consumablesFormRowsRemoveRow(rowIndex) {
  consumablesFormRows.value.splice(rowIndex, 1);
}

var consumablesNameToSelected = "";

function updateConsumableNames(row) {

  // 当消耗品类型发生变化时，更新消耗品名称选项列表
  row.name = null; // 重置消耗品名称的值
}


function getConsumableNames(type) {

  // 根据消耗品类型获取对应的消耗品名称选项列表
  return consumablesName.value[type.id] || [];
}

function getConsumablesUnit(type){
  return consumablesUnit.value[type.id] || [];
}


</script>


<template xmlns="http://www.w3.org/1999/html">
  <div class="mb-8">
    <span class="title">碳减排效益计算
    </span>
    <span class="subtitle">废弃饮料纸基复合包装资源化利用
    </span>
  </div>

  <div class="mb-4 grid grid-cols-12 gap-6">
    <va-card class="col-span-12 row justify-space-between">
      <va-card-content>
        <span class="company px-2">{{ t("company.name") }}</span>
        <va-button class="save-button" @click="saveCompany">
          <va-icon name="check" />
          {{ t("company.save") }}
        </va-button>
      </va-card-content>
    </va-card>
  </div>


  <div class="form-elements grid grid-cols-12 gap-6">
    <va-card class="col-span-12">
      <va-card-title>{{ t("company.basicinfo") }}</va-card-title>
      <va-card-content>
        <form>
          <div class="grid grid-cols-12 gap-6">
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form1.Name" placeholder="请输入企业名称" label="企业名称" />
            </div>

            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-select
                v-model="form1.ProvenceSelected"
                label="省份选择"
                text-by="description"
                track-by="id"
                :options="ProvenceOptions"
              />
            </div>

            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form1.code" placeholder="请输入社会信用代码" label="统一社会信用代码" />
            </div>


            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form1.telephone" placeholder="请输入联系电话" label="联系电话" />
            </div>


            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form1.email" placeholder="请输入联系邮箱" label="联系邮箱" />
            </div>

            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form1.address" placeholder="请输入联系地址" label="联系地址" />
            </div>
          </div>
        </form>
      </va-card-content>
    </va-card>
  </div>

  <div class="my-8">
    <VaDivider />
  </div>

  <div class="form-elements grid grid-cols-12 gap-6">
    <va-card class="col-span-12">
      <va-card-title>{{ t("company.report") }}</va-card-title>
      <va-card-content>
        <form>
          <div class="grid grid-cols-12 gap-6">
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form2.reportYear" placeholder="请输入汇报年份" label="汇报年份" />
            </div>

            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-select
                v-model="form2.craftsmanship"
                label="工艺选择"
                text-by="description"
                track-by="id"
                :options="CraftOptions"
              />
            </div>

            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="form2.total" placeholder="请输入汇报年度回收总量" label="汇报年度回收总量" />
            </div>
          </div>
        </form>
      </va-card-content>
    </va-card>
  </div>


  <div class="my-8">
    <VaDivider />
  </div>


  <div class="form-elements grid grid-cols-12 gap-6">
    <va-card class="col-span-12">
      <va-card-title>{{ t("menu.transportation") }}</va-card-title>
      <va-card-content>
        <div class="flex row-span-1">
          <va-select
            v-model="form3.calculation"
            label="计算方式选择"
            text-by="description"
            track-by="id"
            :options="CalculationOptions"
          />
        </div>
      </va-card-content>
      <va-card-content>
        <form v-if="form3.calculation.id === 1">
          <div v-for="(row, rowIndex) in basicFormRows" :key="rowIndex">
            <div class="grid grid-cols-12 gap-6">
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.start" label="始发地" />
              </div>
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.end" label="终点站" />
              </div>
              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.trans"
                  label="运输方式"
                  text-by="description"
                  track-by="id"
                  :options="transMethod"
                />
              </div>

              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.fuel"
                  label="燃料类型"
                  text-by="description"
                  track-by="id"
                  :options="fuelType"
                />
              </div>
              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-input v-model="row.volume" label="燃料消耗量(L)" />
              </div>

              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-input v-model="row.mileage" label="运输里程(km)" />
              </div>

              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.times" label="运输次数" />
              </div>

              <va-button @click="basicFromRemoveRow(rowIndex)">
                <va-icon name="md_close" />
                删除
              </va-button>

            </div>
            <br>
          </div>
          <!-- 添加新行按钮 -->
          <va-button class="flex" @click="basicFormAddRow">
            <va-icon name="check" />
            添加
          </va-button>
          <!--            <button type="button" @click="addRow">添加新行</button>-->
        </form>

        <form v-if="form3.calculation.id === 2">
          <div v-for="(row, rowIndex) in unitEnergyFormRows" :key="rowIndex">
            <div class="grid grid-cols-12 gap-6">
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.start" label="始发地" />
              </div>
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.end" label="终点站" />
              </div>
              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.trans"
                  label="运输方式"
                  text-by="description"
                  track-by="id"
                  :options="transMethod"
                />
              </div>

              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.fuel"
                  label="燃料类型"
                  text-by="description"
                  track-by="id"
                  :options="fuelType"
                />
              </div>
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.mileage" label="运输里程(km)" />
              </div>

              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.weight" label="运输重量(t)" />
              </div>

              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.times" label="运输次数(t)" />
              </div>

              <va-button @click="unitEnergyFormRemoveRow(rowIndex)">
                <va-icon name="md_close" />
                删除
              </va-button>

            </div>
            <br>
          </div>
          <!-- 添加新行按钮 -->
          <va-button class="flex" @click="unitEnergyFormAddRow">
            <va-icon name="check" />
            添加
          </va-button>
          <!--            <button type="button" @click="addRow">添加新行</button>-->
        </form>

        <form v-if="form3.calculation.id === 3">
          <div v-for="(row, rowIndex) in unitMileageFormRows" :key="rowIndex">
            <div class="grid grid-cols-12 gap-6">
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.start" label="始发地" />
              </div>
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.end" label="终点站" />
              </div>
              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.trans"
                  label="运输方式"
                  text-by="description"
                  track-by="id"
                  :options="transMethod"
                />
              </div>

              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.fuel"
                  label="燃料类型"
                  text-by="description"
                  track-by="id"
                  :options="fuelType"
                />
              </div>
              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.mileage" label="运输里程(km)" />
              </div>

              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.times" label="运输次数(t)" />
              </div>

              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-input v-model="row.fuelPer" label="百公里油耗(L/100km)" />
              </div>

              <div class="flex md:col-span-1 sm:col-span-6 col-span-12">
                <va-input v-model="row.resource" label="数据来源" />
              </div>

              <va-button @click="unitMileageFormRemoveRow(rowIndex)">
                <va-icon name="md_close" />
                删除
              </va-button>

            </div>
            <br>
          </div>
          <!-- 添加新行按钮 -->
          <va-button class="flex" @click="unitMileageFormAddRow">
            <va-icon name="check" />
            添加
          </va-button>
          <!--            <button type="button" @click="addRow">添加新行</button>-->
        </form>
      </va-card-content>
    </va-card>
  </div>


  <div class="my-8">
    <VaDivider />
  </div>


  <div class="form-elements grid grid-cols-12 gap-6">
    <va-card class="col-span-12">
      <va-card-title> 消耗品信息</va-card-title>
      <va-card-content>
        <form>
          <div v-for="(row, rowIndex) in consumablesFormRows" :key="rowIndex">
            <div class="grid grid-cols-12 gap-6">
              <div class="flex md:col-span-3 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.type"
                  @update:modelValue="() => updateConsumableNames(row)"
                  label="消耗品类型"
                  text-by="description"
                  track-by="id"
                  :options="consumablesType"
                />
              </div>

              <div class="flex md:col-span-3 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.name"
                  label="消耗品名称"
                  searchable
                  text-by="description"
                  track-by="id"
                  :options="getConsumableNames(row.type)"
                />
              </div>

              <div class="flex md:col-span-3 sm:col-span-6 col-span-12">
                <va-select
                  v-model="row.unit"
                  label="消耗品单位"
                  text-by="description"
                  track-by="id"
                  :options="getConsumablesUnit(row.type)"
                />
              </div>
              <div class="flex md:col-span-2 sm:col-span-6 col-span-12">
                <va-input v-model="row.consumption" label="消耗量" />
              </div>

              <va-button @click="consumablesFormRowsRemoveRow(rowIndex)">
                <va-icon name="md_close" />
                删除
              </va-button>

            </div>
            <br>
          </div>
          <!-- 添加新行按钮 -->
          <va-button class="flex" @click="consumablesFormRowsAddRow">
            <va-icon name="check" />
            添加
          </va-button>
          <!--            <button type="button" @click="addRow">添加新行</button>-->
        </form>
      </va-card-content>
    </va-card>
  </div>


</template>


<style scoped lang="scss">
.title {
  font-size: 2.5rem;
  color: royalblue;
}

.subtitle {
  font-size: 1rem;
  color: royalblue;
}

.company {
  margin-top: 20px;
  font-size: 1.5rem;
}

.save-button {
  float: right;
  //margin-right: 10px;
  //margin-bottom: 10px;
  //margin-top: 10px;
}


</style>
