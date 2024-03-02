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
        <span class="company px-2">{{t ("company.name")}}</span>
        <va-button class="save-button"><va-icon name="check"/> {{t ("company.save")}}</va-button>
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
      <va-card-title>{{ t("company.moveinfo") }}</va-card-title>
      <va-card-content>
        <form>
          <div class="grid grid-cols-12 gap-6">
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="simple" placeholder="Text Input" />
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="withIcon" placeholder="Input With Icon">
                <template #prepend>
                  <va-icon color="gray" name="envelope" />
                </template>
              </va-input>
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="withButton" placeholder="Input With Button">
                <template #append>
                  <va-button style="margin-right: 0" small> UPLOAD</va-button>
                </template>
              </va-input>
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="successfulEmail" type="email" label="Email (Validated with success)" success>
              </va-input>
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="clearableText" placeholder="Input With Clear Button" clearable />
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input
                v-model="wrongEmail"
                type="email"
                label="Email (Validated)"
                error
                :error-messages="errorMessages"
              >
              </va-input>
            </div>
            <div class="flex md:col-span-4 sm:col-span-6 col-span-12">
              <va-input v-model="withDescription" placeholder="Text Input (with description)" :messages="messages" />
            </div>
          </div>
        </form>
      </va-card-content>
    </va-card>
  </div>

</template>


<script setup lang="ts">
import { ref } from "vue";
import { useI18n } from "vue-i18n";
import { reactive } from 'vue';

const { t } = useI18n();

const form1 = reactive({
  Name: "",
  NameLabel: t("company.from1.name"),
  selected:"",
  code:"",
  ProvenceSelected: "",
  telephone: "",
  email: "",
  address: ""
});


const chosenCountry = ref('')
const simple = ref('')
const withIcon = ref('')
const withButton = ref('')
const withDescription = ref('')
const clearableText = ref('Vasili Savitski')
const successfulEmail = ref('andrei@dreamsupport.io')
const wrongEmail = ref('andrei@dreamsupport')
const messages = ref([
  'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor ' +
  'incididunt ut labore et dolore magna aliqua.',
])
const errorMessages = ref(['Field should contain a valid email'])


const ProvenceOptions = ref([
  {
    id: 1,
    description: '北京',
  },
  {
    id: 2,
    description: '天津',
  },
  {
    id: 3,
    description: '河北',
  },
  {
    id: 4,
    description: '山西',
  },
  {
    id: 5,
    description: '内蒙古',
  },
  {
    id: 6,
    description: '山东',
  },
  {
    id: 7,
    description: '辽宁',
  },
  {
    id: 8,
    description: '吉林',
  },
  {
    id: 9,
    description: '吉林',
  },
  {
    id: 10,
    description: '黑龙江',
  },
  {
    id: 11,
    description: '上海',
  },
  {
    id: 12,
    description: '江苏',
  },
  {
    id: 13,
    description: '浙江',
  },
  {
    id: 14,
    description: '安徽',
  },
  {
    id: 15,
    description: '河南',
  },
  {
    id: 16,
    description: '湖北',
  },
  {
    id: 17,
    description: '湖南',
  },
  {
    id: 18,
    description: '重庆',
  },
  {
    id: 19,
    description: '四川',
  },
  {
    id: 20,
    description: '广东',
  },
  {
    id: 21,
    description: '广西',
  },
  {
    id: 22,
    description: '贵州',
  },
  {
    id: 23,
    description: '云南',
  },
  {
    id: 24,
    description: '海南',
  },
  {
    id: 25,
    description: '陕西',
  },
  {
    id: 26,
    description: '甘肃',
  },
  {
    id: 27,
    description: '青海',
  },
  {
    id: 28,
    description: '宁夏',
  },
  {
    id: 29,
    description: '新疆',
  },
])

const YearOptions = ref([
  {
    id: 1,
    description: "2018年",
  },
  {
    id: 2,
    description: "2019年",
  },
  {
    id: 3,
    description: "2020年",
  },
  {
    id: 4,
    description: "2021年",
  },
  {
    id: 5,
    description: "2022年",
  },
  {
    id: 6,
    description: "2023年",
  },
  {
    id: 7,
    description: "2024年",
  },
]);

const CraftOptions = ref([
  {
    id: 1,
    description: "分离式工艺",
  },
  {
    id: 2,
    description: "一体式加工",
  },
])

</script>




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
