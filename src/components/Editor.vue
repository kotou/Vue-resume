<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" :class="{avctive:currentTap === i}" @click="currentTap = i">
                    <svg class="icon">
                        <use :xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <!--<li v-for="i in [0,1,2,3,4,5]" :class="{avctive:currentTap === i}">tab{{i+1}}</li>-->
            <li :class="{avctive:currentTap === 0}">
                <workExperienceEditor :profile="profile"></workExperienceEditor>
            </li>
            <li :class="{avctive:currentTap === 1}">
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
            </li>
            <li :class="{avctive:currentTap === 2}">
                <h2>学习经历</h2>
            </li>
            <li :class="{avctive:currentTap === 3}">
                <h2>项目经历</h2>
            </li>
            <li :class="{avctive:currentTap === 4}">
                <h2>获奖情况</h2>
            </li>
            <li :class="{avctive:currentTap === 5}">
                <h2>联系方式</h2>
            </li>
        </ol>
    </div>
</template>

<script>
    import workExperienceEditor from './workExperienceEditor.vue'
    export default {
        components: {workExperienceEditor},
        data() {
            return {
                currentTap: 0,
                icons: ['identity', 'experience', 'book', 'project', 'prize', 'phone'],
                profile: {
                    name: '',
                    city: '',
                    birth: ''
                },
                workExperience: [
                    { company: '', content: '' }
                ]
            }
        },
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
        created() {
        }
    }
</script>
<style lang='scss'>
    #editor {
        min-height: 100px;
        display: flex;

        >nav {
            background: #000;
            width: 80px;
            >ol>li {
                padding: 16px 0;
                text-align: center;
                >.icon {
                    width: 24px;
                    height: 24px;
                    fill: white;
                }
                &.avctive {
                    background: #fff;
                    >.icon {
                        fill: #000;
                    }
                }
            }
        }
        >.panes {
            flex: 1;

            >li {
                display: none;
                padding: 32px;
                height: 100%;
                overflow: auto;
                .wrap {
                    position: relative;
                    >.el-icon-close {
                        position: absolute;
                        right: 0;
                        top: 0;
                    }
                }
                &.avctive {
                    display: block;
                }
            }
        }
    }
</style>