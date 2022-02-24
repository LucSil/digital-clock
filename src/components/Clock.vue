<template>
  <div class="digital">
    <div class="day">
      <span class="dayName">{{ dayName }}</span
      >,
      <span class="month">{{ month }}</span>
      <span clas="dayNum">{{ dayNum }}</span
      >,
      <span class="year">{{ year }}</span>
    </div>
    <div class="time">
      <span class="hr">{{ hr }}</span
      >:<span class="min">{{ min }}</span
      >:<span class="sec">{{ sec }}</span
      ><span :class="[ampm == 'AM' ? 'am' : 'pm']">{{ ampm }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hr: "",
      min: "",
      sec: "",
      ampm: "",
      dayName: "",
      dayNum: "",
      month: "",
      year: "",

      week: ["Sun", "Mon", "Tue", "Wed", "Thur", "Fri", "Sat"],
      months: [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec",
      ],
    };
  },

  methods: {
    updateTime: function () {
      let d = new Date();

      //day
      this.dayName = this.week[d.getDay()];
      this.dayNum = d.getDate();
      this.month = this.months[d.getMonth()];
      this.year = d.getFullYear();

      //time
      this.hr = d.getHours();
      this.min = d.getMinutes() < 10 ? `0${d.getMinutes()}` : d.getMinutes();
      this.sec = d.getSeconds() < 10 ? `0${d.getSeconds()}` : d.getSeconds();
      this.ampm = this.hr > 12 ? "pm" : "am";
    },
  },
  mounted() {
    setInterval(() => {
      this.updateTime();
    }, 1000);
  },
};
</script>

<style>
.digital {
  font-family: Cursive;
  font-size: 1.5rem;
  display: grid;
  place-items: center;
  grid-template-rows: repeat(2, 1fr);
  box-shadow: 2px 3px 10px 0px rgba(0, 0, 0, 0.4);
  border-radius: 5px;
}
.day {
  color: rgb(211, 208, 208);
  padding: 10px 20px;
  background: rgb(1, 30, 37);
  border-top-right-radius: 5px;
  border-top-left-radius: 5px;
}

.dayName {
  color: white;
  font-size: 2.5rem;
  font-weight: 600;
}

.month {
  margin: 0 10px 0 5px;
}
.year {
  margin-left: 5px;
}
.time {
  border-bottom-right-radius: 5px;
  border-bottom-left-radius: 5px;
  font-size: 2rem;
}
.hr {
  font-weight: 800;
  margin-right: 5px;
}
.min,
.sec {
  margin: 0 5px;
}
</style>
