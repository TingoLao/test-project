
<template>
    <el-containner>
        <div class="checkBox">
            <div class="title">{{ step.title }}</div>
            <div class="description">{{ step.description }}</div>

            <div class="check-box-input">
                <span></span>
            </div>
            <!-- 遍历生成input -->
            <div id="inputBox">
                <div v-for="item in inputs" :key="item.name" class="inputBoxItem">
                    <span class="inputBoxItem__label">
                        {{ `${item.name}：` }}
                    </span>
                    <input v-model="item.value" class="inputBoxItem__input" :type="item.type" :name="item.name" />
                </div>
            </div>
            <!-- 遍历生成input -->

            <button @click="submit">step3按钮</button>
        </div>
    </el-containner>
</template>

<script>
import jsonData from "../assets/static/step.json";
import { defineComponent } from "vue";

export default defineComponent({
    data() {

        const sendgrid = {
            send_email() {
                if (this.inputs.length > 0) {
                    const formData = this.inputs.reduce((map, input) => {
                        return {
                            ...map,
                            [input.name]: input.value,

                        }
                    }, {});
                } else {
                    const formData = this.inputs.reduce((map, input) => {
                        return {
                            ...map,
                            [input.name]: input.value,

                        }
                    }, {});
                }

            }
        }

        const step = jsonData.steps[2].step3
        const inputs = step.inputs;

        return {
            step,
            inputs,
            sendgrid,
        }
    },

    mounted() {
        // this.createInputBox()

    },

    methods: {
        submit() {
            const formData = this.inputs.reduce((map, input) => {
                return {
                    ...map,
                    [input.name]: input.value
                }
            }, {});

            console.log('exec_jscode_with_formData', formData);
            alert(eval(this.step.js_code))
        },

        createInputBox() {
            const step = jsonData.steps[0].step1


            for (const key in step.inputs) {
                const inputObj = step.inputs[key]
                let inpt = document.createElement('input')
                let inptBox = document.getElementById('inpt_form')
                switch (parseInt(key)) {
                    case 0:
                        inptBox = document.getElementById('inpt_sub')
                        // 创建subject的input框
                        break;
                    case 1:
                        inptBox = document.getElementById('inpt_form')
                        break;
                    case 2:
                        inptBox = document.getElementById('inpt_to')
                        break;
                    case 3:
                        inptBox = document.getElementById('body_text')
                }
                inpt.name = inputObj.name
                inpt.type = inputObj.type
                inpt.value = inputObj.value
                console.log(inptBox);
                inptBox.append(inpt)
                // console.log(inputBox);
            }
        },

        // createInputBox() {
        //     const step = jsonData.steps[0].step1

        //     const inputBox = document.getElementById('inputBox')
        //     // console.log(inputBox);
        //     for (const key in step.inputs) {
        //         const inputObj = step.inputs[key]
        //         // console.log(inputObj);
        //         let inpt = document.createElement('input')
        //         inpt.name = inputObj.name
        //         inpt.type = inputObj.type
        //         inpt.value = inputObj.value
        //         // console.log(inpt.value);
        //         inputBox.append(inpt)
        //         // console.log(inputBox);
        //     }
        // }
    },


})




</script>

<style scoped>
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

#textarea {
    width: 90%;
    min-height: 100px;
    overflow: scroll;
    overflow-wrap: break-word;
}

.inputBoxItem {
    display: flex;
    align-items: center;
    margin-top: 4px;
}

.inputBoxItem__label {
    width: 100px;
}

.inputBoxItem__input[type=textarea] {
    width: 75%;
    min-height: 60px;
    line-height: 12px;
}
</style>