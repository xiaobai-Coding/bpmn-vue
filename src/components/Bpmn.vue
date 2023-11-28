<template>
    <div class="containers">
        <div ref="canvasRef" class="canvas"></div>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import BpmnModeler from 'bpmn-js/lib/Modeler'
import xmlStr from '../mock/xmlStr'
const canvasRef = ref(null)
const BpmnModel = ref(null)
const createNewDiagram = () => {
          // 将字符串转换成图显示出来
    BpmnModel.value.importXML(xmlStr, (err) => {
    if (err) {
        // console.error(err)
    } else {
        // 这里是成功之后的回调, 可以在这里做一系列事情
    }
    })
}
const initBpmn = () =>{
    BpmnModel.value = new BpmnModeler({
        container: canvasRef.value
    })
    createNewDiagram()
}
onMounted(()=>{
    initBpmn()
})
</script>

<style lang="scss" scoped>
    .containers {
        background-color: #f0eded;
        width: 100%;
        height: 100%;
    }
    .canvas {
            width: 100%;
            height: 100%;
        }
</style>