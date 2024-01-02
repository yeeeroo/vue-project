<script>
// import MyButton from '@/components/custom/MyButton.vue';
import CalcButton from '@/components/custom/CalcButton.vue';

export default {
  components: {
    CalcButton,
  },
  // 放置所有變數的位置
  data() {
    return {
      numA: 0,
      numB: 0,
      result: 0,
      html: `
      <div>
        123
      </div>`,
      calcType: ['+', '-', '*', '/'],
    };
  },
  // 放置所有function的位置
  methods: {
    // add() {
    //   // 先判斷numA numB 不為空
    //   if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
    //   this.result = this.numA + this.numB;
    // },
    // reduce() {
    //   if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
    //   this.result = this.numA - this.numB;
    // },
    // times() {
    //   if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
    //   this.result = this.numA * this.numB;
    // },
    // divide() {
    //   if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
    //   this.result = this.numA / this.numB;
    // }
    calcNumber(type) {
      if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
      switch (type) {
        case '+':
          this.result = this.numA + this.numB;
          break;
        case '-':
          this.result = this.numA - this.numB;
          break;
        case '*':
          this.result = this.numA * this.numB;
          break;
        case '/':
          this.result = this.numA / this.numB;
          break;
      }
    },
  },
}
</script>

<template>
  <!-- v-if -->
  <!-- v-else-if -->
  <!-- v-else -->

  <!-- v-show -->

  <!-- v-for 記得要補:key -->

  <!-- v-html 最常用於所見即所得編輯器 -->

  <!-- v-bind 省略的寫法":" -->
  <!-- v-model => input與變數的連結 -->

  <!-- v-on 省略的寫法"@" 後面連接觸發的事件名稱 -->
  <div class="calc">
    計算機
    <div v-html="html"></div>
    <div >
      <label>
        數字A:
        <!-- v-model -->
        <input v-model="numA" type="number">
      </label>
    </div>
    <div>
      <label>
        數字B:
        <input v-model="numB" type="number">
      </label>
    </div>

    <div class="btns">
      <!-- <button class="btn" type="button" @click="add()">
        +
      </button> -->
      <!-- 如何將資料傳進components -->
      <!-- 如何從components取得資料 -->
      <CalcButton :calc-type="calcType" />
      <!-- <MyButton @click="add()">
        <template #placeA>+</template>
        <template #placeB>我是另一個開孔</template>
      </MyButton>
      <MyButton @click="reduce()">-</MyButton>
      <MyButton @click="times()">*</MyButton>
      <MyButton @click="divide()">/</MyButton>
    </div> -->
    </div>
    <div class="output">
      輸出結果: {{ result }}
    </div>
  </div>
</template>

<!-- scoped: 目的是為了不要影響到其他區塊的style -->
<style scoped>
.btns {
  display: flex;
  gap: 30px;
}

.btn {
  padding: 5px 10px;
}
</style>
