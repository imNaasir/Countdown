<template>
  <main class="flex flex-col items-center justify-center gap-4  h-screen">
    <section class="flex flex-col justify-center content-center text-center text-3xl  uppercase">
      <div>
        <span class="text-[#6c5ffc]">countdown </span>timer
      </div>
    </section>
    <section class="text-6xl flex justify-center content-center mx-auto ">
      <div class="relative mr-2  pb-5">
        <div class="flip-card text-sm">
          <div class="top ">{{ displayDays }}</div>
          <div class="bottom">{{ displayDays }}</div>
        </div>
        <div class="absolute text-xs left-1/2 -translate-x-1/2 bottom-0 text-[#9088d4]">days</div>
      </div>
      <!-- <span>:&nbsp;</span> -->
      <div class="relative mr-2 ">
        <div class="flip-card">
          <div class="top">{{ displayHours }}</div>
          <div class="bottom">{{ displayHours }}</div>
        </div>
        <div class="absolute text-xs left-1/2 -translate-x-1/2 bottom-0 text-[#9088d4]">hours</div>
      </div>
      <!-- <span>:&nbsp;</span> -->
      <div class="relative mr-2 ">
        <div class="flip-card">
          <div class="top">{{ displayMinutes }}</div>
          <div class="bottom">{{ displayMinutes }}</div>
        </div>
        <div class="absolute text-xs left-1/2 -translate-x-1/2 bottom-0 text-[#9088d4]">minutes</div>
      </div>
      <!-- <span>:&nbsp;</span> -->
      <div class="relative mr-2 ">
        <div class="flip-card">
          <div class="top">{{ displaySeconds }}</div>
          <div class="bottom">{{ displaySeconds }}</div>
        </div>
        <div class="absolute text-xs left-1/2 -translate-x-1/2 bottom-0 text-[#9088d4]">seconds</div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      displayDays: 0,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0,
    }
  },
  components: {
    seconds() {
      return 1000
    }
  },
  methods: {
    showRemaining() {
      const timer = setInterval(() => {
        // let currentTime = new Date();
        // let endTime = new Date(2023, 9, 16, 10, 10, 10, 10);
        // let diff = endTime.getTime() - currentTime.getTime()
        // console.log(diff)
        const currentYear = new Date().getFullYear();
        let newYearTime = new Date(`january 1 ${currentYear + 1} 00:00:00`)
        let currentTime = new Date();
        let diff = newYearTime - currentTime
        // console.log(diff);

        if (diff < 0) {
          clearInterval(timer)
        };

        const d = Math.floor(diff / 1000 / 60 / 60 / 24)
        const h = Math.floor((diff / 1000 / 60 / 60) % 24)
        const m = Math.floor((diff / 1000 / 60) % 60)
        const s = Math.floor((diff / 1000) % 60)
        // console.log(d)

        this.displayDays = d < 10 ? "0" + d : d;
        this.displayHours = h < 10 ? "0" + h : h;
        this.displayMinutes = m < 10 ? "0" + m : m;
        this.displaySeconds = s < 10 ? "0" + s : s;;
        //console.log(this.displayDays)

      }, 1000);
    }
  },
  mounted() {
    this.showRemaining();
  },

}
</script>

<style>
*,
*::after,
*::before {
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 2.25rem;
}


body {
  background-color: #f0f0f5;
  height: 100vh important;
}

.flip-card {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  box-shadow: 0 2px 3px 0 rgba(0, 0, 0, .2);
  border-radius: .1em;
  color: #6c5ffc;
}

.top,
.bottom {
  height: .75em;
  line-height: 1;
  padding: .25em;
  overflow: hidden;
}

.top {
  background-color: #f7f7f7;
  border-top-right-radius: .1em;
  border-top-left-radius: .1em;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}

.bottom {
  background-color: white;
  display: flex;
  align-items: flex-end;
  border-bottom-right-radius: .1em;
  border-bottom-left-radius: .1em;
}</style>