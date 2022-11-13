<script>
import users from "../components/index.json"

export default{
  data(){
    return{
    index: -1,
    data:{}
  }
  },
  methods: {
    goNext() {
      this.data = users[++this.index] || users[this.index=0]
    },
    goBack() {
      this.data = users[users.length] || users[this.index--]
    }
  }
}
</script>



<template>
  <div class="d-flex"> <button class="btn btn-outline-info mx-1" @click="goNext">Next</button><button class="btn btn-outline-info mx-1" @click="goBack">Prev</button></div>
  <div class="flex mx-auto max-w-5xl shadow-lg">
    <!-- leftSide panel start from here -->
    <div class="leftSide bg-slate-200">
      <img class="object-cover w-full img-fluid h-80 " id="profile" :src="data.image" alt="Modern building architecture" />
      <!-- skills area -->
      <div class="pb-5">
        <div class="pt-3 px-5 text-lg ">
          <div class="">
            <h3 class="uppercase text-xl text-sky-600 font-semibold">Skills/Proficiency </h3>
            <div class="text-black">
              <div class="d-flex">
                <p>Proficient</p>
                –
                <p>Intermediate</p>
                –
                <p>Basic</p>
              </div>
              <p>
                &nbsp;&nbsp;+++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+
              </p>
            </div>
            <p v-for="item of data.skills" class="text-black">{{ item.name }} ({{ item.level === 'Proficient' ? "+++" : item.level === 'Intermediate' ? '++' : '+' }})</p>
          </div>
          <div class="block">
            <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Tools </h3>
            <p class="text-black" v-for="item of data.tools">{{ item }}</p>
          </div>
          <div class="block">
            <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Awards & Certifications </h3>
            <p class="text-black mb-2" v-for="item of data.awardsAndCertifications">
            <p>{{ item.certification }}</p>
            <p class="italic">{{ item.startDate }} - {{ item.endDate }}</p>
            </p>
          </div>
          <div class="block">
            <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Volunteer work & interest </h3>
            <p class="text-black mb-2" v-for="item of data.volunteerWork">
            <p class="font-bold">{{ item.role }}</p>
            <p>{{ item.work }}</p>
            </p>
          </div>
          <div class="block">
            <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Languages </h3>
            <div class="text-black ">
              <p>Native – Fluent – Basic</p>
              <p>
                &nbsp;+++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+
              </p>
            </div>
            <p class="text-black" v-for="item of data.languages">
            <p>{{ item.name }} ({{ item.level === 'Native' ? "+++" : item.level === 'Fluent' ? '++' : '+' }})</p>
            </p>
          </div>
        </div>
      </div>
    </div>
    <!-- leftSide panel ends here -->
    <!-- rightSide panel start from here -->
    <div class="rightSide">
      <div class="p-3 w-full h-80 nameSide">
        <div class="w-full pr-10 mt-3 d-flex justify-content-end">
          <img class="img-fluid w-40 h-20 object-contain" src="./amalitech logo.png" alt="" />
        </div>
        <div class="mt-16 ml-10 text-4xl">
          <h1 class="block fs-1 leading-tight font-bold text-white " id="name">{{ data.firstName }}</h1>
          <p class=" fs-3 font-medium " id="title">{{ data.jobTitle }}</p>
        </div>
      </div>

      <!-- A block of Work Experience -->
      <div class="pt-3 px-16 md:px-16 sm:px-10 text-lg ">
        <div class="">
          <div class="uppercase tracking-wide text-xl text-sky-600 font-bold mb-3">Work Experience</div>
          <div class="" v-for="item of data.workExperience">
            <span class="block mt-4 text-lg leading-tight font-bold text-black ">{{ item.jobTitle }}</span>
            <div class="">
              <p class="mt-1 text-black  ">
              <p>{{ item.jobLocation }}</p>
              <p class="text-black  italic">{{ item.startDate }} - {{ item.endDate }}</p>
              </p>
            </div>
            <div v-for="list of item.jobDescription" class="">
              <ul class="list-disc pl-10 text-black ">
                <li>{{ list }}</li>
              </ul>
            </div>
          </div>
        </div>

        <!-- A block of Education -->
        <div class="mt-5">
          <div class="uppercase tracking-wide text-xl text-sky-600 mb-3 font-bold">Education</div>
          <div class="mb-4" v-for="item of data.education">
            <span class="block mt-4 text-lg leading-tight text-black  font-bold">{{ item.Programme }}</span>
            <p class="mt-1 text-black ">
              <span>Institution:</span>
              {{ item.institution }}
            <p class="text-black italic">Year of Graduation: {{ item.yearGrad }}</p>
            </p>
            <div class="" v-for="list of item.specialization">
              <ul class="list-disc pl-10 text-black ">
                <li>{{ list }}</li>
              </ul>
            </div>
          </div>
        </div>
        <!-- block of Work ends here -->
      </div>
      <!-- rightSide panel ends here -->
    </div>
  </div>
  </template>

<style>
.nameSide {
  background-color: #0C4767;
  color: #E1E1E1;
}

.rightSide {
  flex: 4;
}

.leftSide {
  flex: 2;
}
</style>