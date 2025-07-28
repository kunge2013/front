<template>
  <div class="flex-properties-demo">
    <h2>Flex 项目属性演示</h2>
    
    <div class="controls">
      <div>
        <label>flex-grow:
          <input type="range" v-model="flexGrow" min="0" max="5"> {{ flexGrow }}
        </label>
      </div>
      <div>
        <label>flex-shrink:
          <input type="range" v-model="flexShrink" min="0" max="5"> {{ flexShrink }}
        </label>
      </div>
      <div>
        <label>flex-basis:
          <input type="range" v-model="flexBasis" min="50" max="300"> {{ flexBasis }}px
        </label>
      </div>
      <div>
        <label>align-self:
          <select v-model="alignSelf">
            <option value="auto">auto</option>
            <option value="flex-start">flex-start</option>
            <option value="flex-end">flex-end</option>
            <option value="center">center</option>
            <option value="baseline">baseline</option>
            <option value="stretch">stretch</option>
          </select>
        </label>
      </div>
    </div>
    
    <div class="flex-container">
      <div class="flex-item" v-for="n in 3" :key="n">Item {{ n }}</div>
      <div 
        class="flex-item special-item"
        :style="{
          flexGrow,
          flexShrink,
          flexBasis: flexBasis + 'px',
          alignSelf
        }"
      >
        特殊项目
      </div>
      <div class="flex-item" v-for="n in 3" :key="n + 3">Item {{ n + 3 }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FlexDemo',
  data() {
    return {
      flexGrow: 0,
      flexShrink: 1,
      flexBasis: 100,
      alignSelf: 'auto'
    }
  }
}
</script>

<style scoped>
.flex-properties-demo {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.controls {
  margin-bottom: 20px;
  padding: 15px;
  background-color: #f5f5f5;
  border-radius: 5px;
}

.controls > div {
  margin-bottom: 10px;
}

.flex-container {
  display: flex;
  gap: 10px;
  padding: 20px;
  background-color: #f0f0f0;
  border: 1px solid #ddd;
  min-height: 200px;
}

.flex-item {
  padding: 15px;
  background-color: #42b983;
  color: white;
  text-align: center;
  flex: 1 1 100px;
}

.special-item {
  background-color: #e91e63;
}
</style>