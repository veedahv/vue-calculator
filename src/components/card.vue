<template>
  <div class="grid-box">
    <div class="calculator">
      <div class="input-box">
        <p class="input-calc">{{ printValue }}</p>
        <input
          type="text"
          class="input-screen"
          :value="screenValue"
          placeholder="0"
          disabled
        />
      </div>
      <div class="keypad-box grid">
        <div class="operator-box grid">
          <button class="keypad" :disabled="isDisabled" @click="addFun">+</button>
          <button class="keypad" :disabled="isDisabled" @click="subFun">-</button>
          <button class="keypad" :disabled="isDisabled" @click="mulFun">x</button>
          <button class="keypad" :disabled="isDisabled" @click="divideFun">/</button>
        </div>
        <div class="keypad-no-box grid">
          <button class="keypad" @click="numberFun" v-for="n in 9" :key="n">
            {{ n }}
          </button>
        </div>
        <div class="calc-box grid">
          <button class="keypad clear-btn" @click="clearFun">ac</button>
          <button class="keypad del-btn" :disabled="isDisabled" @click="delFun">del</button>
          <button class="keypad" @click="numberFun">0</button>
        </div>
        <div class="clear-box">
          <button class="keypad" :disabled="isDisabled" @click="calcFun">=</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
  data() {
    return {
      printValue: "0",
      screenValue: "",
      sumValue: 0,
      operator: "add",
      isDisabled: true,
    };
  },
  computed: {
    performFun() {
      let returnSum;
      switch (this.operator) {
        case "add":
          returnSum = parseInt(this.sumValue) + parseInt(this.screenValue);
          break;
        case "sub":
          returnSum = parseInt(this.sumValue) - parseInt(this.screenValue);
          break;
        case "divide":
          returnSum = parseInt(this.sumValue) / parseInt(this.screenValue);
          break;
        case "multiply":
          returnSum = parseInt(this.sumValue) * parseInt(this.screenValue);
          break;

        default:
          break;
      }
      return returnSum;
    },
  },
  methods: {
    numberFun(e) {
      let noValue = e.target.innerText;
      this.screenValue = this.screenValue + noValue;
      this.isDisabled = false;
    },
    addFun() {
      this.sumValue = this.performFun;
      this.operator = "add";
      this.screenValue = "";
      this.printValue = this.sumValue + " +";
      this.isDisabled = true;
    },
    subFun() {
      this.sumValue = this.performFun;
      this.operator = "sub";
      this.screenValue = "";
      this.printValue = this.sumValue + " -";
      this.isDisabled = true;
    },
    divideFun() {
      this.sumValue = this.performFun;
      this.operator = "divide";
      this.screenValue = "";
      this.printValue = this.sumValue + " /";
      this.isDisabled = true;
    },
    mulFun() {
      this.sumValue = this.performFun;
      this.operator = "multiply";
      this.screenValue = "";
      this.printValue = this.sumValue + " x";
      this.isDisabled = true;
    },
    calcFun() {
      this.sumValue = this.performFun;
      this.operator = "add";
      this.printValue = this.sumValue;
      this.screenValue = "";
      this.sumValue = 0;
      this.isDisabled = true;
    },
    delFun() {
      this.screenValue = this.screenValue.slice(0, -1);
      if (this.screenValue.length === 0) {
        this.isDisabled = true;
      }
    },
    clearFun() {
      this.printValue = "0";
      this.screenValue = "";
      this.sumValue = 0;
      this.operator = "add";
      this.isDisabled = true;
    },
  },
};
</script>

<style scoped>
.calculator {
  box-sizing: border-box;
  max-width: 370px;
  margin: 10px auto;
  padding: 25px 15px;
  /* background: #e3e3e3;
  border: 2px solid #dad7d7; */
  /* background: #c7c5c5;
  border: 2px solid #dad7d7; */
  background: #d6e0f0;
  border: 2px solid #8d93ab;
  border-radius: 12px;
}

.input-box {
  text-align: right;
  padding: 10px;
  font-size: 14px;
  background: #ffffff;
  margin-bottom: 15px;
}

.input-screen {
  font-size: 24px;
  text-align: right;
  border: none;
  outline: none;
  width: 100%;
  /* background: #FAFAFA; */
  background: #ffffff;
}

.keypad {
  width: 100%;
  padding: 12px;
  box-shadow: 3px 4px 5px rgba(0, 0, 0, 0.2);
  border: none;
  outline: none;
  font-size: 20px;
  border-radius: 5px;
  font-family: 'Akaya Telivigala', cursive;
  /* background: #ffffff; */
  /* background: #979696; */
  background: #8d93ab;
  color: #ffffff;
}
.del-btn {
  background: #ff0000;
  text-transform: capitalize;
}
.clear-btn {
  background: #00ff00;
  text-transform: uppercase;
}

.keypad:hover {
  box-shadow: 3px 4px 5px rgba(0, 0, 0, 0.2);
  transform: scale(1.02);
}

.keypad:active {
  box-shadow: 3px 4px 5px rgba(0, 0, 0, 0.2);
  transform: scale(1.005);
}

.grid {
  display: grid;
  gap: 12px;
}
.keypad-box {
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
.operator-box {
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-column: 1 / 5;
  grid-row: 4 / 5;
}

.keypad-no-box {
  grid-template-columns: 1fr 1fr 1fr;
  grid-column: 1 / 4;
  grid-row: 1 / 4;
}
.calc-box {
  grid-template-columns: 1fr;
  grid-column: 4 / 5;
  grid-row: 1 / 4;
}
.clear-box {
  grid-column: 1 / 5;
  grid-row: 5 / 6;
}
</style>

