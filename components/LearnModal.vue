<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask" @click="$emit('close')">
      <div class="modal-wrapper">
        <div
          class="modal-container w-screen bg-neutral-50 p-4 shadow sm:w-[576px] sm:rounded-lg text-neutral-900"
        >
          <h3 class="uppercase text-xl font-black mb-2">
            About this Macro Calculator
          </h3>
          <p class="mb-3">
            Your estimated calorie needs are given by this macro calculator. It
            is better to start with the suggested caloric intake. Try these
            calories for one to two weeks, then adjust as necessary to meet your
            specific needs.
          </p>
          <p class="mb-8 font-medium italic">
            For optimal results, please consult a qualified nutritionist.
          </p>
          <p class="font-bold mb-2">
            How to choose your activity level on this Macro Calculator
          </p>
          <p class="mb-3">
            Your degree of physical activity must be evaluated before
            calculating the number of calories your body needs to achieve your
            specific goal.
          </p>
          <p class="mb-3">
            Your Total Daily Energy Expenditure (TDEE) is affected by a number
            of factors, exercise being only one of them. You should also take
            into account how much you move and how active you are in your daily
            life and at work. Your Non-Exercise Activity Thermogenesis (NEAT),
            which has a significantly greater impact on TDEE than exercise, is
            what this is.
          </p>
          <p class="mb-6">
            When using the calculator, you can select from Low, Medium, or High
            levels of exercise.
          </p>
          <p class="font-bold mb-2">Choosing your level of activity</p>
          <p class="mb-3">
            If your job is sedentary and you exercise little to nothing, you
            should choose a
            <span class="font-medium underline underline-offset-2"
              >low activity level</span
            >. Examples of sedentary jobs include office work, being a
            receptionist, driving, etc.
          </p>
          <p class="mb-3">
            If you lead a moderate lifestyle, which can include working a
            standing desk job and exercising three to four times per week or
            working a sedentary job but exercising four to five times per week,
            you should choose the
            <span class="font-medium underline underline-offset-2"
              >medium activity level</span
            >. Even if you work from home and rarely exercise, you should still
            choose a medium activity level. The following are examples of
            standing jobs: restaurant servers, security guards, and sales
            assistants.
          </p>
          <p class="mb-6">
            If you exercise 3-5+ times a week and have a physically demanding
            work, you should choose the
            <span class="font-medium underline underline-offset-2"
              >High Activity Level</span
            >
            option. Carpenters, tradespeople, paramedics, and other occupations
            that require constant movement or being on your feet are some
            instances of this.
          </p>

          <button
            class="uppercase mb-2 flex w-full justify-center rounded-md bg-rose-600 py-2 px-2 font-bold text-white shadow-sm hover:bg-rose-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-rose-600"
            @click="$emit('close')"
          >
            Close
          </button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup lang="ts">
defineProps<{
  show: Boolean;
}>();
</script>
