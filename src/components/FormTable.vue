<template>
  <div class="main">
    <div class="status_bar">
      <span class="time_style">
        <a class="time">9:41</a>
      </span>
      <span class="mobile_signal">
        <img class="signal" src="../assets/MobileSignal.png" />
      </span>
      <span class="wifi">
        <img class="Wifi" src="../assets/Wifi.png" />
      </span>
      <span class="battery">
        <img class="Battery" src="../assets/Battery.png" />
      </span>
    </div>
    <div class="head">
      <header>Today</header>
      <span class="more">
        <img class="More" src="../assets/More.png" @click="showModal = true" />
      </span>
      <Form
        v-on:submitItem="submit"
        v-if="showModal"
        @close="showModal = false"
      />
    </div>
    <div id="body">
      <li v-for="(item, index) in details" v-bind:key="index">
        <div id="container">
          <div class="check">
            <label class="container">
              <input type="checkbox" />
              <span class="checkmark"></span>
            </label>
          </div>
          <div class="item">
            {{ item.todo }}
            <div id="icons" v-if="index == 1">
              <img class="clock_icon" src="../assets/clock_icon.png" />
              <span id="time">7:00pm</span>
            </div>
          </div>
          <div class="spot">
            <span
              class="dot"
              v-bind:style="{
                'background-color':
                  colors[Math.floor(Math.random() * colors.length)],
              }"
            ></span>
          </div>
        </div>
        <hr />
      </li>
    </div>
    <div class="indicator">
      <img class="rectangular_bar" src="../assets/Rectangle.png" />
    </div>
  </div>
</template>

<script>
import Form from "./Form.vue";
export default {
  name: "FormTable",
  components: {
    Form,
  },
  data() {
    return {
      showModal: false,
      colors: ["#6EDEA4", "#B677FC", "#EC5C6E", "FFFFFF"],
      details: [
        {
          todo: "Start making a presentation",
        },
        {
          todo: "Pay for rent",
        },
        {
          todo: "Buy a milk",
        },
        {
          todo: "Don’t forget to pick up Mickael from school",
        },
        {
          todo: "Buy a chocolate for Charlotte",
        },
      ],
    };
  },

  methods: {
    submit(value) {
      this.details.push({
        todo: value,
      });
    },
  },
};
</script>
<style>
@font-face {
  font-family: "SFProDisplay";
  src: url("~@/fonts/SF-Pro-Display-Bold.woff");
}
@font-face {
  font-family: "SFProText";
  src: url("~@/fonts/sf-pro-text-medium.woff");
}

.status_bar {
  position: relative;
  width: 100%;
  height: 44px;
  margin-bottom: 58px;
}
.time_style {
  position: absolute;
  left: 1.7%;
  top: 27.27%;
  bottom: 25%;
}
.time {
  position: absolute;
  left: 0%;
  right: 0%;
  top: 9.52%;
  bottom: 4.76%;

  font-family: SF Pro Text;
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 18px;
  /* identical to box height */

  display: flex;
  align-items: flex-end;
  text-align: center;
  letter-spacing: -0.02em;
  color: #252a31;
}
.mobile_signal {
  position: absolute;
  left: 93.6%;
  top: 40.15%;
  bottom: 35.61%;
}
.signal {
  width: 17px;
  height: 10.67px;
}
.wifi {
  position: absolute;
  left: 95.95%;
  top: 39.39%;
  bottom: 35.69%;
}
.Wifi {
  width: 15.27px;
  height: 10.97px;
}
.battery {
  position: absolute;
  right: 0%;
  top: 39.39%;
  bottom: 34.85%;
}
.Battery {
  width: 24.33px;
  height: 11.33px;
}
.main {
  padding: 10px;
}

.head {
  list-style-type: none;
  overflow: hidden;
  margin-top: 18px;
}

header {
  float: left;
  font-family: SFProDisplay;
  font-size: 32px;
  line-height: 41px;
  letter-spacing: 0.01em;
  color: #252a31;
}
.more {
  position: absolute;
  width: 25px;
  height: 25px;
  right: 19px;
}
.More:hover {
  cursor: pointer;
}

#body {
  margin-top: 30px;
}

li {
  list-style-type: none;
}

hr {
  border-top: 1px;
  margin-top: 18px;
  margin-left: 50px;
}

.container {
  display: flex;
  position: relative;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}
/* Create a custom checkbox */
.checkmark {
  align-self: center;
  position: absolute;
  height: 25px;
  width: 25px;
  border: 2px solid #dadada;
  border-radius: 15px;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #2196f3;
}

/* Create the tick (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked .checkmark:after {
  display: block;
}

/* Style the tick */
.container .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}

#container {
  display: flex;
  padding-top: 14px;
  align-items: center;
}

.item {
  flex: 90%;
  margin-left: 50px;
  font-family: SFProText;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.02em;
  color: #252a31;
}

.check {
  text-align: center;
}

.spot {
  text-align: center;
  margin-right: 8px;
}
#icons {
  display: flex;
  padding-top: 2px;
}

#time {
  font-family: SFProText;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: -0.337647px;
  color: #252a31;
  mix-blend-mode: normal;
  opacity: 0.3;
  margin-left: 15px;
}

.dot {
  display: block;
  height: 12px;
  width: 12px;
  border-radius: 50%;
}

.indicator {
  position: absolute;
  height: 34px;
  left: 0px;
  right: 0px;
  bottom: 0px;
}
.rectangular_bar {
  position: absolute;
  left: 45%;
  right: 45%;
  top: 58.82%;
  bottom: 26.47%;
  border-radius: 100px;
}
.clock_icon {
  position: absolute;
  width: 16px;
  height: 16px;
  left: 60px;
  margin-left: 5px;
}
@media screen and (max-width: 1140px) {
  .mobile_signal {
    left: 91.3%;
  }
  .wifi {
    left: 94.35%;
  }
  .rectangular_bar {
    left: 44.5%;
  }
}
@media screen and (max-width: 900px) {
  .time_style {
    left: 2.5%;
  }
  .mobile_signal {
    left: 89.85%;
  }
  .wifi {
    left: 93.35%;
  }
  .rectangular_bar {
    left: 42.7%;
  }
}

@media screen and (max-width: 710px) {
  .time_style {
    left: 3.35%;
  }
  .mobile_signal {
    left: 87.6%;
  }
  .wifi {
    left: 91.95%;
  }
  .rectangular_bar {
    left: 41%;
  }
}

@media screen and (max-width: 600px) {
  .time_style {
    left: 3.7%;
  }
  .mobile_signal {
    left: 84.6%;
  }
  .wifi {
    left: 89.95%;
  }
  .rectangular_bar {
    left: 37.6%;
  }
}

@media screen and (max-width: 450px) {
  .time_style {
    left: 5%;
  }
  .mobile_signal {
    left: 75.6%;
  }
  .wifi {
    left: 83.95%;
  }
  .rectangular_bar {
    left: 33%;
  }
}
</style>
