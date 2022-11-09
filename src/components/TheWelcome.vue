<script setup>
import data from "../components/index.json"
</script>

<template>
   <div v-if="data" class="col-12">
      <div class="mx-auto">
        <!-- photo and name pane -->
        <div class="mx-auto bg-white mt-3 shadow-sm overflow-hidden max-w-5xl">
          <div class="flex text-dark">
            <div class="d-flex justify-content-center align-items-center">
              <div class="h-80 w-96 bg-gray-500">
                <img class="object-cover  h-80 w-96" id="profile"
                  :src="data?.image"
                  alt="Modern building architecture"/>
              </div>
            </div>
            <div class="p-3 w-full nameSide">
              <div class="w-full pr-10 mt-6 d-flex justify-content-end">
                <img class="object-cover h-18 w-30" src="https://amalitech.com/wp-content/uploads/2020/04/amali-services-white-01-294x84.png" alt=""/>
              </div>
              <div class="mt-16 ml-10 text-4xl">
                <h1 class="block fs-1 leading-tight font-bold text-white " id="name">Reuben</h1>
                <p class=" fs-3 font-medium " id="title">Senior UI/UX Designer</p>
              </div>
            </div>
          </div>
        </div>
        <!-- photo and name pane ends here -->
        <!-- skills and work experience starts here -->
        <div class="mx-auto bg-white mt-2 shadow-sm overflow-hidden max-w-5xl">
          <div class="flex text-dark">
            <div class="d-flex justify-content-center align-items-center
              bg-slate-200">
              <div class="h-full w-96 p-3">
                <div  class="block">
                  <h3 class="uppercase tracking-wide text-xl text-sky-600
                    font-semibold">Skills/Proficiency </h3>
                  <div class="">
                    <div class="d-flex">
                      <p>Proficient</p>
                      –
                      <p>Intermediate</p>
                      –
                      <p>Basic</p>
                    </div>
                  </div>
                  <p>
                    &nbsp;&nbsp;+++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+
                  </p>
                  <p v-for="item of data.skills" class="text-slate-600">{{item.name}} ({{item.level==='Proficient'?"+++":item.level==='Imtermediate'?'++':'+'}})</p>
                </div>
                <div class="block">
                  <h3 class="uppercase tracking-wide text-xl text-sky-600
                    font-semibold mt-3">Tools </h3>
                  <p class="text-slate-600" v-for="item of data.tools">{{item}}</p>
                </div>
                <div class="block">
                  <h3 class="uppercase tracking-wide text-xl text-sky-600
                    font-semibold mt-3">Awards & Certifications </h3>
                  <p class="text-slate-600 mb-2" v-for="item of data.awardsAndCertifications">
                    <p>{{item.certification}}</p>
                    <p class="italic">{{item.startDate}} - {{item.endDate}}</p>
                  </p>
                </div>
                <div class="block">
                  <h3 class="uppercase tracking-wide text-xl text-sky-600
                    font-semibold mt-3">Volunteer work & interest </h3>
                  <p class="text-slate-600 mb-2" v-for="item of data.volunteerWork">
                    <p class="font-bold">{{item.role}}</p>
                    <p>{{item.work}}</p>
                  </p>
                </div>
                <div class="block">
                  <h3 class="uppercase tracking-wide text-xl text-sky-600
                    font-semibold mt-3">Languages </h3>
                    <div class="text-slate-500">
                      <p>Native – Fluent – Basic</p>
                      <p>
                        &nbsp;+++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;++&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;+
                      </p>
                    </div>
                  <p class="text-slate-600" v-for="item of data.languages">
                    <p>{{item.name}} ({{item.level==='Native'?"+++":item.level==='Fluent'?'++':'+'}})</p>
                  </p>
                </div>
              </div>
            </div>
            <div class="pt-3 pl-10">
              <!-- A block of Work Experience -->
              <div class="uppercase tracking-wide text-xl text-sky-600
                font-semibold">Work Experience</div>
                <div class="" v-for="item of data.workExperience">
                  <span class="block mt-1 text-lg leading-tight font-medium
                    text-slate-500">{{item.jobTitle}}</span>
                  <div class="">
                    <p class="mt-1 text-slate-500 ">
                    <p>{{item.jobLocation}}</p>
                    <p class="text-slate-500 italic">{{item.startDate}} - {{item.endDate}}</p>
                    </p>
                  </div>
                  <div v-for="lop of item.jobDescription" class="">
                    <ul class="list-disc pl-10 text-slate-500">
                      <li>{{lop}}</li>
                    </ul>
                  </div>
                </div>
              
              <!-- A block of Education -->
              <div class="uppercase tracking-wide text-xl text-sky-600
                font-semibold mt-5">Education</div>
                <div class="mb-4" v-for="item of data.education">
                  <span class="block mt-1 text-lg leading-tight font-medium
                    text-slate-500">{{item.Programme}}</span>
                  <p class="mt-1 text-slate-500 ">
                    <span>Institution:</span>
                    {{item.institution}}
                    <p class="text-slate-500 italic">{{item.yearGrad}}</p></p>
                  <div class="" v-for="lop of item.specialization">
                    <ul class="list-disc pl-10 text-slate-500" >
                      <li>{{lop}}</li>
                    </ul>
                  </div>
                </div>
            </div>
          </div>
        </div>
        <!-- skills and work experience ends here -->
      </div>
    </div>
</template>

<style>
 .nameSide{
          background-color: #0C4767;
          color: #E1E1E1;
        }
</style>