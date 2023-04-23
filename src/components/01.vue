<template>
    <div>
        <a-steps v-model:current="current" direction="horizontal" labelPlacement="vertical" status="process" @change="ssc">
            <a-step title="Step 1"  v-for="item in steps" :key="item.title" :title="item.title" :subTitle="item.chititle" />
        </a-steps>
        <a-divider />
        <div class="steps-content">
            {{ steps[current].content }}
        </div>
    </div>
</template>
<script>
import { defineComponent, ref } from 'vue';

export default defineComponent({
    setup() {
        const current = ref(0);
        const next = () => {
            current.value++;
        };
        const prev = () => {
            current.value--;
        };
        return {
            current,
            steps: [
                {
                    title: '1次预审会议',
                    chititle: '2022/07/20',
                    content: '内容一',
                },
                {
                    title: '2次预审会议',
                    chititle: '2022/08/13',
                    content: '内容二'
                },
                {
                    title: '预审结束(通过)',
                    content: '内容三',
                },
            ],

            next,
            prev,
        };
       
    }, 
    created(){

    }
    ,
    methods:{
        ssc(current){
            console.log(current);
        }
    }
});
</script>
<style scoped lang="less">
/deep/.ant-steps-item-process > .ant-steps-item-container > .ant-steps-item-content > .ant-steps-item-title {
    color: rgba(0, 128, 255, 0.85);
}
</style>