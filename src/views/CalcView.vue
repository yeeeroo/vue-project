<script>
export default {
  // 放置所有變數的位置
  data() {
    return {
      numA: 0,
      numB: 0,
      result: 0,
    };
  },
  // 放置所有function的位置
  methods: {
    add() {
      // 先判斷numA numB 不為空
      if (this.numA.toString().trim() === '' || this.numB.toString().trim() === '') return;
      this.result = this.numA + this.numB;
    },
  },
}
</script>

<template>
  <div class="calc">
    計算機
    <div>
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
      <button class="btn" type="button" @click="add()">
        +
      </button>
      <button class="btn" type="button">-</button>
      <button class="btn" type="button">*</button>
      <button class="btn" type="button">/</button>
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
