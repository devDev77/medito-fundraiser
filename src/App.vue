<script setup>
import { onMounted, ref, computed } from 'vue';


// const progress = ref(80)
const funded = ref('23,300')
const goal = ref('50,000')

const progress = computed(() => {
  console.log(parseFloat(funded.value.split(",").join("")) / parseFloat(goal.value.split(",").join("")))
  return Math.ceil(parseFloat(funded.value.split(",").join("")) / parseFloat(goal.value.split(",").join("")) * 100)
})

const mounted = ref(false)

function scrollToElement() {
  const [el] = this.$refs.last;
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
}

onMounted(() => {
  setTimeout(() => {
    mounted.value = true
  }, 700)
})

</script>

<template>
  <div class="h-screen flex items-center justify-center">
    <div class="container h-screen">
      <p class="absolute mt-[8%] text-2xl">Medito Foundation</p>
      <h1 class="text-6xl mt-[20%] "><span class="border font-bold border-solid border-8 border-emerald-300 p-3">Current
          Goal</span> <span class="pl-5 font-bold">Make Meditation Mandatory or smth</span></h1>
      <h3 class="text-4xl mt-[8%] ml-[10%] font-medium leading-loose">Just a quick overview about the problem at hand, yk yk Lorem ipsum, dolor sit amet consectetur adipisicing elit. Enim quaerat neque atque expedita, reprehenderit, sint corrupti tenetur iure fuga blanditiis eaque. Rem iure exercitationem ullam fugit! Provident, nisi est! Adipisci.</h3>

      <div id="progressBar" class="w-[100%] grid mt-[17%] h-12 border border-double border-black">
        <span class="absolute justify-self-end mr-2 text-2xl self-center">{{ progress }}%</span>
        <div class="h-11 ease-out bg-emerald-300 transition-all duration-500  
                " :style="[mounted ? { 'width': progress + '%' } : { 'width': 0 }]"></div>
      </div>

      <div class="grid">
        <h3 class="text-3xl mt-3 ">Raised ${{ funded }} out of ${{ goal }}</h3>
        <div class="justify-self-center">
          <button
            class="border border-emerald-300 border-solid border-4 hover:bg-emerald-400 transition-all hover:scale-110 text-3xl inline mr-16 mt-10 font-bold w-36 p-4 rounded-full ">Donate</button>
          <button
            class="border border-emerald-300 border-solid border-4 hover:bg-emerald-400 transition-all hover:scale-110 text-3xl inline mr-16 mt-10 font-bold w-40 p-4 rounded-full ">Q&A</button>

        </div>
      </div>
    </div>
  </div>

  <!-- <div class="grid w-screen">
    <div class="container">
      <h1 class="text-6xl">Q&A</h1>

    </div>
  </div> -->
</template>

<style >
@keyframes fadeInUp {
  0% {
    transform: translateY(100%);
    opacity: 0;
  }

  100% {
    transform: translateY(0%);
    opacity: 1;
  }
}

h1,
h3,
#progressBar,
button,
p {
  animation: 1s fadeInUp;
}
</style>
