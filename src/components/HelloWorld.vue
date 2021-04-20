<template>
<div>
  <div class="bg-white">
    <header class="space-y-2 border-b border-gray-200 px-6">
      <nav class="max-w-5xl mx-auto flex item-center justify-between pt-3">
        <div class="flex items-center space-x-3">
          <span>
            <a href="#">
              <svg xmlns="http://www.w3.org/2000/svg"
             xmlns:xlink="http://www.w3.org/1999/xlink" 
             aria-hidden="true"
             focusable="false" width="2em" height="2em" 
             style="-ms-transform: rotate(360deg); -webkit-transform: rotate(360deg); transform: rotate(360deg);"
             preserveAspectRatio="xMidYMid meet" viewBox="0 0 24 24">
             <path d="M24 22.525H0l12-21.05l12 21.05z" fill="black"/>
             </svg>
            </a>
          </span>
          <span>
            <svg viewBox="0 0 32 32" stroke="currentColor" className= "text-block" 
            class="h-8 w-8 text-gray-200">
              <line x1="8" y1="28" x2="24" y2="4"/>
            </svg>
          </span>
            <AccountSwitcher></AccountSwitcher>
        </div>
        <div class="inline-flex items-center space-x-4 ml-5">
          <div class="inline-flex items-center space-x-5">
             <button type="button" 
              class="border rounded-md border-gray-200 px-3 py-1.5 text-gray-600 text-sm hover:border-black trasition ease-in-out duration-150">
              Feedback
              </button>
          <a href="#" class="text-sm leading-5 text-gray-500 hover:text-black">Blog</a>
          <a href="#" class="text-sm leading-5 text-gray-500 hover:text-black">Support</a>
          <a href="#" class="text-sm leading-5 text-gray-500 hover:text-black"> Docs</a>
          </div>
          <button type="button">
            <DotsHorizontalIcon class="h-5 w-5 text-gray-400 hover:text-black"></DotsHorizontalIcon>
          </button>
          <button>
             <img class=" rounded-full h-8 w-8 border border-gray-200"
             src="data:image/jpeg;base64,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" alt="">
          </button>
           
        </div>
      </nav>
        <div class=" max-w-5xl mx-auto px-6">
          <nav class="-mb-px flex text-sm leading-5 space-x-5 ">
          <a href="#" class="py-3 border-b-2 border-black px-1 text-gray-500 hover:text-black trasition ease-in-out duration-150">Overview</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500 px-1 hover:text-black trasition ease-in-out duration-150">Projects</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500 px-1 hover:text-black trasition ease-in-out duration-150">Integrations</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500 px-1 hover:text-black trasition ease-in-out duration-150">Activity</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500 px-1 hover:text-black trasition ease-in-out duration-150">Domains</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500  px-1 hover:text-black trasition ease-in-out duration-150">Usage</a>
          <a href="#" class="py-3 border-b-2 border-transparent text-gray-500 px-1 hover:text-black trasition ease-in-out duration-150">Settings</a>
          </nav>
        </div>
    </header>
    <div class="max-w-5xl mx-auto px-6 items-start pt-14 pb-28 flex justify-between">
      <div class="flex space-x-8">
        <div>
          <img class=" rounded-full h-24 w-24 border border-gray-200"
          src="data:image/jpeg;base64,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" alt="">
        </div>
        <div class="space-y-5">
          <div class="flex items-center space-x-4">
            <h1 class="text-4xl leading-10 font-bold">Fafemi Adeola</h1>
            <span class="mt-1 inline-flex text-xs leading-5 text-black font-medium rounded-full px-2 bg-gray-50 border border-gray-200 tracking-wide uppercase">
              Hobby</span>
          </div>
          <div>
            <dt class="text-xs leading-5 font-medium text-gray-500 uppercase">Git integration</dt>
            <dd class="text-sm leading-s font-medium inline-flex items-center space-x-2">
              
              <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" focusable="false" width="1em" height="1em" style="-ms-transform: rotate(360deg); -webkit-transform: rotate(360deg); transform: rotate(360deg);" preserveAspectRatio="xMidYMid meet" viewBox="0 0 16 16">
              <g fill="black">
              <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59c.4.07.55-.17.55-.38c0-.19-.01-.82-.01-1.49c-2.01.37-2.53-.49-2.69-.94c-.09-.23-.48-.94-.82-1.13c-.28-.15-.68-.52-.01-.53c.63-.01 1.08.58 1.23.82c.72 1.21 1.87.87 2.33.66c.07-.52.28-.87.51-1.07c-1.78-.2-3.64-.89-3.64-3.95c0-.87.31-1.59.82-2.15c-.08-.2-.36-1.02.08-2.12c0 0 .67-.21 2.2.82c.64-.18 1.32-.27 2-.27c.68 0 1.36.09 2 .27c1.53-1.04 2.2-.82 2.2-.82c.44 1.1.16 1.92.08 2.12c.51.56.82 1.27.82 2.15c0 3.07-1.87 3.75-3.65 3.95c.29.25.54.73.54 1.48c0 1.07-.01 1.93-.01 2.2c0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/>
              </g>
              <rect x="0" y="0" width="32" height="32" fill="rgba(0, 0, 0, 0)" /></svg>
              <span>kojusola</span>
              </dd>
          </div>
        </div>
      </div>
      <div class="grid grid-cols-2 gap-x-6">
        <a href="#" class="inline-flex justify-center rounded border border-gray-200 text-sm leading-5 px-6 py-2 bg-white text-gray-500 font-medium hover:border-black hover:text-black transition ease-in-out duration-150">Invite Team</a>
        <a href="#" class="inline-flex justify-center border border-transparent rounded text-sm leading-5 px-6 py-2 text-white bg-black hover:border-black hover:text-black hover:bg-white transition ease-in-out duration-150">Import Project</a>
      </div>
    </div>
  </div>
  <div class="border-t border-gray-200 mb-8">
    <main class="-mt-9 max-w-5xl mx-auto px-6 grid grid-cols-12 gap-x-20">
    <div class="col-span-7">
      <h2 class="sr-only">Recent Projects</h2>
      <div class="space-y-12">
        <ul class="space-y-12">
        <ProjectCard></ProjectCard>
        <ProjectCard></ProjectCard>
        <ProjectCard></ProjectCard>
        <ProjectCard></ProjectCard>
      </ul>
      <div>
        <a href="#" class="text-sm leading-5 font-bold text-blue-500 hover:underline"> View all Projects</a>
      </div>
      </div>
    </div>
    <div class="col-span-5 pt-1 space-y-9">
      <h2 class="text-sm leading-5 font-bold">
        Recent Activity
      </h2>
      <div class="space-y-12">
        <ul class=" border-b border-gray-200 divide-y divide-gray-200">
        <Activity activity="logged in Via GitHub" date="26d"></Activity>
        <Activity activity="logged in Via GitHub" date="50d"></Activity>
        <Activity activity="logged in Via GitHub" date="90d"></Activity>
        <Activity activity="logged in Via GitHub" date="91d"></Activity>
        <Activity activity="logged in Via GitHub" date="93d"></Activity>
        <Activity activity="logged in Via GitHub" date="95d"></Activity>
        <Activity activity="logged in Via GitHub" date="96d"></Activity>
        <Activity activity="logged in Via GitHub" date="97d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
        <Activity activity="logged in Via GitHub" date="99d"></Activity>
      </ul>
      <div>
        <a href="#" class="text-sm leading-5 font-bold text-blue-500 hover:underline"> View all Activity</a>
      </div>
      </div>
    </div>
  </main>
  </div>
</div>

</template>

<script>
import { DotsHorizontalIcon } from "@vue-hero-icons/outline";
import ProjectCard from './projectCard'
import Activity from './activity'
import AccountSwitcher from './accountswitcher'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    activity: String,
    date: String
  },
  components: {DotsHorizontalIcon,ProjectCard,Activity,AccountSwitcher}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
