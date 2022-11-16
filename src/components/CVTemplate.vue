<script>
import users from "../components/index.json"

export default{
  data(){
    return{
    index: -1,
    data:{},
    show: true
  }
  },
  methods: {
    goNext() {
      this.data = users[++this.index] || users[this.index=0]
    },
    goBack() {
      this.data = users[users.length] || users[--this.index] || users[this.index=0]
    },
    generatePDF() {
      window.print();
    }
  },
  mounted() {
    this.goNext();
  },
}
</script>

<template>
  <div>
    <div class="d-flex mb-3 bgg mt-5">
      <button class="btn btn-outline-info mx-1" @click="goBack">Prev</button>
      <button class="btn btn-outline-info mx-1" @click="goNext">Next</button>
      <button class="btn btn-outline-info mx-1" @click="generatePDF">Print</button>
    </div>
    <div class="mx-auto max-w-5xl " id="pdf">
    <!-- leftSide panel start from here -->
    
    <div class="d-flex bg-slate-200">
      <div class="left">
        <img class="profile" :src="data.image" alt="Modern building architecture" />
      </div>

      <div class="u-info-pane">
        <div class="w-full d-flex justify-content-end">
          <img class="logoimg" src="./amalitech logo.png" alt="logo" />
          <!-- <img class="logoimg" src="https://amalitech.com/wp-content/uploads/2020/04/amali-services-white-01-300x86.png" alt="" /> -->
        </div>
        <div class="px-10 pt-4 text-4xl">
          <h1 class="block fs-1 leading-tight font-bold text-white " id="name">{{ data.firstName }}</h1>
          <p class=" fs-3 font-medium " id="title">{{ data.jobTitle }}</p>
        </div>
      </div>
    </div>

    <div class="d-flex">
     <!-- skills area -->
     <div class=" leftr bg-slate-200 px-2">
        <div class="pt-3 p-3 text-lg ">
          <div class="">
            <h3 class="uppercase text-xl text-sky-600 font-semibold">Skills/Proficiency </h3>
        
             <div v-for="item of data.skills" class="text-black">
              {{ item.name }} {{ item.level === 'Proficient' ? "+++" : item.level === 'Intermediate' ? '++' : '+' }}
            </div> 
          </div>
          <div class="block">
            <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Tools </h3>
            <div class="text-black" v-for="item of data.tools">{{ item }}</div>
          </div>
          <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Awards & Certifications </h3>
          <div v-for="item in data.awardsAndCertifications" class="block">
            <p class="text-black mb-2">
            <p>{{ item.certification }}</p>
            <p class="italic">{{ item.startDate }} - {{ item.endDate }}</p>
            </p>
          </div>
          <h3 class="uppercase tracking-wide text-xl text-sky-600 font-semibold mt-3">Volunteer work & interest </h3>
          <div class="block" v-for="item of data.volunteerWork">
            <p class="text-black mb-2">
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
            <div class="text-black" v-for="item of data.languages">
            <p>{{ item.name }} ({{ item.level === 'Native' ? "+++" : item.level === 'Fluent' ? '++' : '+' }})</p>
            </div>
          </div>
        </div>
      </div>

      <!-- A block of Work Experience -->
      <div class="pt-3 rightr p-10 bg-white text-lg ">
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
  </div>
</template>

<style>
.primage{
  width: 20%;
  -webkit-print-color-adjust: "exact",
}
.u-info-pane{
  width: 70%;
  background-color: #0C4767;
  color: #E1E1E1;
  padding-right: 25px;
}

.bgc{
  background-color: #0C4767;
  color: #E1E1E1;
}
.logoimg{
  height: 120px;
  width: 380px;
  object-fit: contain;
}
.profile{
  width: 100%;
  height:280px;
  object-fit: cover; 
}
.left{
  width: 30%;
}
.right{
  width: 70%;
}

.leftr{
  width: 30%;
}
.rightr{
  width: 70%;
}

@media print {
   .bgg{
    display: none !important;
   }
   
   @page  
{ 
    size: A4 !important;   /* auto is the initial value */ 

    /* this affects the margin in the printer settings */ 
    margin: 5px 0px 20px 0px;  
} 

body  
{ 
    /* this affects the margin on the content before sending to printer */ 
    margin: 0px;  

} 

}
</style>
