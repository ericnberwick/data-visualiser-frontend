<template>
  <div>
    <section>
      <!-- Container -->
      <div class="mx-auto max-w-7xl px-5 py-16 text-center md:px-10 md:py-20">
        <!-- Component -->
        <h2 class="text-3xl font-bold md:text-5xl">AilmentAnalyzer: Decode Your Health</h2>
        <p class="mx-auto mb-8 mt-4 max-w-2xl text-gray-500 md:mb-12 lg:mb-16"> To get started, simply enter your
          symptoms in the provided input field below. Be as specific as possible, including any additional details such
          as duration or severity. Once you’ve listed your symptoms, click the "Analyze" button, and our advanced
          algorithm will evaluate your input to predict potential conditions. </p>
        <!-- Form -->
        <form name="wf-form-name" method="get" class="mx-auto mb-4 text-left sm:px-4 md:px-20">
          <div class="mb-4 grid w-full grid-cols-2 gap-6">
            <div>
              <label htmlFor="name-2" class="mb-1 font-medium"> First Name </label>
              <input type="text" v-model="firstName"
                class=" block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black"
                placeholder="" required="" />
            </div>
            <div>
              <label htmlFor="name-3" class="mb-1 font-medium"> Last Name </label>
              <input type="text" v-model="lastName"
                class=" block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black"
                placeholder="" required="" />
            </div>
          </div>
          <div class="mb-4">
            <label htmlFor="field" class="mb-1 font-medium"> Age </label>
            <input type="text" v-model="age"
              class="mb-4 block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black" />
          </div>
          <div class="mb-4">
            <label htmlFor="field" class="mb-1 font-medium"> Occupation </label>
            <input type="text" v-model="occupation"
              class="mb-4 block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black" />
          </div>
          <div class="mb-4">
            <label htmlFor="field" class="mb-1 font-medium"> Pre exisiting health conditions </label>
            <input type="text" v-model="preExistingHealthConditions"
              class="mb-4 block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black" />
          </div>
          <div class="mb-4">
            <label htmlFor="field" class="mb-1 font-medium"> Hours of exercise per week </label>
            <input type="text" v-model="hoursOfExercisePerWeek"
              class="mb-4 block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black" />
          </div>
          <div class="mb-4">
            <label htmlFor="field" class="mb-1 font-medium"> Symptoms </label>
            <input type="text" v-model="symptoms"
              class="mb-4 block h-9 w-full rounded-md border border-solid border-black px-3 py-6 text-sm text-black" />
          </div>
          <div class="mb-5 md:mb-6 lg:mb-8">
            <label htmlFor="field" class="mb-1 font-medium"> Description of problem </label>
            <textarea placeholder="" maxLength="5000" name="field" v-model="descriptionOfProblem"
              class="mb-2.5 block h-auto min-h-44 w-full rounded-md border border-solid border-black px-3 py-2 text-sm text-black"></textarea>
          </div>

          <Button @click="sendDataForAnalysis"
            class="inline-block w-full rounded-md cursor-pointer bg-black px-6 py-3 text-center font-semibold text-white">Analzye</Button>
        </form>
      </div>
    </section>
  </div>
</template>


<script setup>
import { ref } from 'vue'
import axios from 'axios'

const firstName = ref('');
const lastName = ref('');
const age = ref('');
const occupation = ref('')
const preExistingHealthConditions = ref('')
const hoursOfExercisePerWeek = ref('')
const symptoms = ref('')
const descriptionOfProblem = ref('')

const sendDataForAnalysis = async () => {
  try {
    const response = await axios.post('http://suuuuu.com', {
      firstName: firstName.value,
      lastName: lastName.value,
      age: age.value,
      occupation: occupation.value,
      preExistingHealthConditions: preExistingHealthConditions.value,
      hoursOfExercisePerWeek: hoursOfExercisePerWeek.value,
      symptoms: symptoms.value,
      descriptionOfProblem: descriptionOfProblem.value
    });
    console.log('Response:', response.data);
  } catch (error) {
    console.error('Error:', error);
  }
}
</script>