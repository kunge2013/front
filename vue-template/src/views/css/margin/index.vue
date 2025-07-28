<template>
    <div class="margin-demo">
      <h2>Margin 演示 (选项式 API)</h2>
      
      <div class="controls">
        <div>
          <label>上边距: <input type="range" v-model="marginTop" min="0" max="50"> {{ marginTop }}px</label>
        </div>
        <div>
          <label>右边距: <input type="range" v-model="marginRight" min="0" max="50"> {{ marginRight }}px</label>
        </div>
        <div>
          <label>下边距: <input type="range" v-model="marginBottom" min="0" max="50"> {{ marginBottom }}px</label>
        </div>
        <div>
          <label>左边距: <input type="range" v-model="marginLeft" min="0" max="50"> {{ marginLeft }}px</label>
        </div>
      </div>
      
      <div 
        class="demo-box" 
        :style="{
          marginTop: `${marginTop}px`,
          marginRight: `${marginRight}px`,
          marginBottom: `${marginBottom}px`,
          marginLeft: `${marginLeft}px`
        }"
      >
        这是一个演示盒子
      </div>
      
      <div class="result">
        <p>当前 margin 值: {{ computedMargin }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        marginTop: 20,
        marginRight: 20,
        marginBottom: 20,
        marginLeft: 20
      }
    },
    computed: {
      computedMargin() {
        if (this.marginTop === this.marginRight && 
            this.marginRight === this.marginBottom && 
            this.marginBottom === this.marginLeft) {
          return `margin: ${this.marginTop}px`
        } else if (this.marginTop === this.marginBottom && this.marginRight === this.marginLeft) {
          return `margin: ${this.marginTop}px ${this.marginRight}px`
        } else {
          return `margin: ${this.marginTop}px ${this.marginRight}px ${this.marginBottom}px ${this.marginLeft}px`
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .margin-demo {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
  }
  
  .controls {
    margin-bottom: 20px;
    padding: 15px;
    background-color: #f5f5f5;
    border-radius: 5px;
  }
  
  .controls div {
    margin-bottom: 10px;
  }
  
  .demo-box {
    padding: 30px;
    background-color: #42b983;
    color: white;
    border-radius: 5px;
    text-align: center;
    transition: margin 0.3s ease;
  }
  
  .result {
    margin-top: 20px;
    padding: 10px;
    background-color: #eee;
    border-radius: 5px;
  }
  </style>