<template>
    <el-containner>
        <div class="checkBox">
            步骤2 盒子
            <div class="title">{{ step.title }}</div>
            <div class="description">{{ step.description }}</div>

            <div id="inputBox">
                <!-- 遍历生成input -->
                <div v-for="item in inputs" :key="item.name" class="inputBoxItem">
                    <span>{{ `${item.name}：` }}</span>
                    <input v-model="item.value" class="inputBoxItem__input" :type="item.type">
                </div>

            </div>

            <button @click="submit">Step2按钮</button>
        </div>
    </el-containner>
</template>

<script>
import jsonData from "../assets/static/step.json";
import { defineComponent } from "vue";

export default defineComponent({
    data() {
        const step = jsonData.steps[1].step2
        // console.log(step);
        const inputs = step.inputs;
        return {
            step,
            inputs
        }
    },

    mounted() {
        // this.createInputBox()

    },

    methods: {
        createInputBox() {
            const step = jsonData.steps[1].step2

            for (const key in step.inputs) {
                const inputObj = step.inputs[key]
                let inpt = document.createElement('input')
                let span = document.createElement('span')
                span.textContent = inputObj.name
                let inptBox = document.getElementById('')
                switch (parseInt(key)) {
                    case 0:
                        inptBox = document.getElementById('inpt_tags')
                        // 创建subject的input框
                        break;
                    case 1:
                        inptBox = document.getElementById('inpt_limit')

                }
                inpt.name = inputObj.name
                inpt.type = inputObj.type
                inpt.value = inputObj.value
                console.log(inptBox);
                inptBox.append(span)
                inptBox.append(inpt)
                // console.log(inputBox);
            }
        },

        // createInputBox1() {
        //     const step = jsonData.steps[1].step2
        //     const inputBox = document.getElementById('inputBox2')
        //     // console.log(inputBox);
        //     for (const key in step.inputs) {
        //         const inputObj = step.inputs[key]
        //         // console.log(inputObj);
        //         let span = document.createElement('span')
        //         let inpt = document.createElement('input')
        //         span.textContent = inputObj.name
        //         inpt.name = inputObj.name
        //         inpt.type = inputObj.type
        //         inpt.value = inputObj.value
        //         // console.log(inpt.value);
        //         inputBox.append(span)
        //         inputBox.append(inpt)
        //         // console.log(inputBox);
        //     }
        // },
    }
})

</script>

<style>
.checkBox {
    box-sizing: border-box;
    display: inline-block;
    align-items: center;
    width: 80%;
    height: auto;
    padding: 12px;
    border-radius: 3px;
    /* border: 1px solid black; */
    box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px, rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
    overflow: hidden;
}

.inputBoxItem {
    display: flex;
    align-items: center;
    margin-top: 4px;
}

.inputBoxItem__label {
    width: 100px;
}
</style>