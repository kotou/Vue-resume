<template>
    <div>
        <h2>工作经历</h2>
        <div class="wrap" v-for="(work,index) in workExperience">
            <el-form>
                <el-form-item label="公司">
                    <el-input v-model="work.company"></el-input>
                </el-form-item>
                <el-form-item label="工作内容">
                    <el-input v-model="work.content"></el-input>
                </el-form-item>
            </el-form>
            <i class="el-icon-close" @click="removeWorkExperience(index)"></i>
        </div>
        <div style="position: relative;">
            <el-button type="primary" icon="el-icon-plus" @click="addWorkExperience" style="position: absolute;top:0;right:0;"></el-button>
        </div>
    </div>
</template>
<script>
    export default {
        props: ['workExperience'],
        methods: {
            addWorkExperience() {
                this.workExperience.push({
                    company: '', content: ''
                })
            },
            removeWorkExperience(index) {
                this.workExperience.splice(index, 1)
            }
        },
    }
</script>