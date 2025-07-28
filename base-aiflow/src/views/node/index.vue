<template>
  <div id="logic-flow-container"></div>
</template>

<script>
import LogicFlow from '@logicflow/core';

import "@logicflow/core/dist/index.css";

export default {
  data() {
    return {
      data: {
        nodes: [
          {
            id: '21',
            type: 'rect',
            x: 200,
            y: 200,
            text: 'Origin Usage-rect',
            properties: { width: 160, height: 80 }
          },
          {
            id: '50',
            type: 'circle',
            x: 500,
            y: 200,
            text: 'Origin Usage-circle',
            properties: { r: 60 }
          }
        ],
        edges: [
          {
            id: 'rect-2-circle',
            type: 'polyline',
            sourceNodeId: '21',
            targetNodeId: '50'
          }
        ]
      }
    }
  },
  mounted() {
    this.lf = new LogicFlow({
      container: document.querySelector('#logic-flow-container'),
      grid: true,
    });
    this.lf.render(this.data);
  }
}
</script>

<style scoped>
#logic-flow-container {
    margin-left: 10%;
    width : 1300px;
    height: 848px;
    border: 1px solid #eee;
    background: #fafbfc;
}
</style>
