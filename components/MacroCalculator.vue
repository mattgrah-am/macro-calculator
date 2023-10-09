import { LearnModal } from '#build/components';
<template>
  <form @submit.prevent="calculateMacros" v-if="!macrosCalculated" class="">
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-x-4 gap-y-3 mb-6">
      <div>
        <label for="height" class="block text-sm font-medium leading-6"
          >Height (cm)</label
        >
        <input
          id="height"
          name="height"
          type="number"
          v-model="height"
          :required="true"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        />
      </div>
      <div>
        <label for="weight" class="block text-sm font-medium leading-6"
          >Weight (kg)</label
        >
        <input
          id="weight"
          name="weight"
          type="number"
          v-model="weight"
          :required="true"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        />
      </div>
      <div>
        <label for="age" class="block text-sm font-medium leading-6">Age</label>
        <input
          id="age"
          name="age"
          type="number"
          v-model="age"
          :required="true"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        />
      </div>
      <div>
        <label for="gender" class="block text-sm font-medium leading-6"
          >Gender</label
        >
        <select
          id="gender"
          name="gender"
          v-model="gender"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        >
          <option
            v-for="(item, idx) in genderValues"
            :value="item.value"
            :key="idx"
          >
            {{ item.option }}
          </option>
        </select>
      </div>
      <div>
        <label for="activity-level" class="block text-sm font-medium leading-6"
          >Activity Level</label
        >
        <select
          id="activity-level"
          name="activity-level"
          v-model="activityLevel"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        >
          <option
            v-for="(item, idx) in activityLevelValues"
            :value="item.value"
            :key="idx"
          >
            {{ item.option }}
          </option>
        </select>
      </div>
      <div>
        <label for="goal" class="block text-sm font-medium leading-6"
          >Goal</label
        >
        <select
          id="goal"
          name="goal"
          v-model="goal"
          class="w-full rounded-md border-r-4 border-transparent pl-2 py-2 ring-1 ring-neutral-300 shadow-sm text-sm text-neutral-800 focus:outline-none focus:ring focus:ring-rose-600"
        >
          <option
            v-for="(item, idx) in goalValue"
            :value="item.value"
            :key="idx"
          >
            {{ item.option }}
          </option>
        </select>
      </div>
    </div>
    <div>
      <button
        type="submit"
        class="uppercase mb-2 flex w-full justify-center rounded-md bg-rose-600 py-2 px-2 font-bold text-white shadow-sm hover:bg-rose-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-rose-600"
      >
        Calculate
      </button>
    </div>
  </form>
  <div v-if="macrosCalculated">
    <h3 class="uppercase text-xl font-black mb-4">Your Macros</h3>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium">TDEE</div>
      <div>{{ tdee }}kcal</div>
    </div>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium text-rose-500">Target Calories</div>
      <div class="font-medium text-rose-500">{{ deficit }}kcal</div>
    </div>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium">Protein</div>
      <div>{{ protein }}g</div>
    </div>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium">Fat</div>
      <div>{{ fat }}g</div>
    </div>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium">Carbs</div>
      <div>{{ carbs }}g</div>
    </div>
    <div class="flex justify-between mb-4 pb-1 border-b border-neutral-300">
      <div class="font-medium">BMI</div>
      <div>{{ bmi }}</div>
    </div>
    <button
      type="button"
      @click="macrosCalculated = false"
      class="uppercase mb-2 flex w-full justify-center rounded-md bg-rose-600 py-2 px-2 font-bold text-white shadow-sm hover:bg-rose-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-rose-600"
    >
      Back
    </button>
  </div>
  <div class="text-xs flex flex-col sm:flex-row sm:justify-between text-center">
    <button
      type="button"
      @click="showModal = !showModal"
      class="hover:underline uppercase font-semibold hover:text-rose-500 hover:underline-offset-2"
    >
      Learn More
    </button>
    <div>
      Created with ❤️ by
      <NuxtLink
        class=""
        to="https://mattgrah.am/"
        target="_blank"
        :external="true"
        >mattgrah.am
      </NuxtLink>
    </div>
  </div>

  <Teleport to="body">
    <LearnModal :show="showModal" @close="showModal = false" />
  </Teleport>
</template>

<script setup lang="ts">
const height = ref();
const weight = ref();
const age = ref();
const gender = ref("female");
const activityLevel = ref(1.4);
const goal = ref(0.8);
const tdee = ref(0);
const deficit = ref(0);
const protein = ref(0);
const carbs = ref(0);
const fat = ref(0);
const bmi = ref(0);
const macrosCalculated = ref(false);
const showModal = ref(false);

const activityLevelValues = [
  { option: "Low", value: 1.4 },
  { option: "Medium", value: 1.55 },
  { option: "High", value: 1.8 },
];
const goalValue = [
  { option: "Lose", value: 0.8 },
  { option: "Maintain", value: 1 },
  { option: "Gain", value: 1.15 },
];

const genderValues = [
  { option: "Female", value: "female" },
  { option: "Male", value: "male" },
];

const calculateBMI = () => {
  return Math.ceil((weight.value / (height.value * height.value)) * 10000);
};

const calculateMacros = () => {
  tdee.value = Math.ceil(
    ((gender.value === "female" ? 447.362 : 88.362) +
      (gender.value === "female" ? 9.247 : 13.397) * weight.value +
      (gender.value === "female" ? 3.098 : 4.799) * height.value -
      (gender.value === "female" ? 4.33 : 5.699) * age.value) *
      activityLevel.value
  );
  deficit.value = Math.ceil(tdee.value * goal.value);

  bmi.value = calculateBMI();

  if (bmi.value > 40) {
    protein.value = Math.ceil(weight.value);
  } else if (bmi.value > 35) {
    protein.value = Math.ceil(1.2 * weight.value);
  } else if (bmi.value > 30) {
    protein.value = Math.ceil(1.5 * weight.value);
  } else {
    protein.value = Math.ceil(1.8 * weight.value);
  }

  fat.value = Math.ceil(
    weight.value < 75 ? 0.85 * weight.value : 0.7 * weight.value
  );
  carbs.value = Math.ceil(
    (deficit.value - (protein.value * 4 + fat.value * 9)) / 4
  );

  macrosCalculated.value = true;
};
</script>
