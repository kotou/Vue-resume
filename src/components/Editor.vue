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
                <profileEditor :profile="resume.profile"></profileEditor>
            </li>
            <li :class="{avctive:currentTap === 1}">
                <ArrayEditor :items="resume.studyExperience" :labels="{school:'学校',duration:'时间',degree:'学位'}" title="学习经历"></ArrayEditor>
            </li>
            <li :class="{avctive:currentTap === 2}">
                <ArrayEditor :items="resume.workExperience" :labels="{company:'公司',content:'工作内容'}" title="工作经历"></ArrayEditor>
            </li>
            <li :class="{avctive:currentTap === 3}">
                <ArrayEditor :items="resume.projects" :labels="{name: '项目名称', content:'项目内容'}" title="项目经验"></ArrayEditor>
            </li>
            <li :class="{avctive:currentTap === 4}">
                <ArrayEditor :items="resume.awards" :labels="{name: '奖项名称'}" title="获奖情况"></ArrayEditor>
            </li>
            <li :class="{avctive:currentTap === 5}">
                <h2>联系方式</h2>
                <el-form>
                    <el-form-item label="QQ">
                        <el-input v-model="resume.contacts.qq"></el-input>
                    </el-form-item>
                    <el-form-item label="微信">
                        <el-input v-model="resume.contacts.wechat"></el-input>
                    </el-form-item>
                    <el-form-item label="邮箱">
                        <el-input v-model="resume.contacts.email"></el-input>
                    </el-form-item>
                    <el-form-item label="手机">
                        <el-input v-model="resume.contacts.phone"></el-input>
                    </el-form-item>
                </el-form>
            </li>
        </ol>
    </div>
</template>

<script>
    import profileEditor from './profileEditor.vue'
    import ArrayEditor from './ArrayEditor.vue'
    export default {
        components: { profileEditor, ArrayEditor },
        props: ['resume'],
        data() {
            return {
                currentTap: 0,
                icons: ['identity', 'book', 'experience', 'project', 'prize', 'phone']
            }
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