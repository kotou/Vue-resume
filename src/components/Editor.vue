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
                <profileEditor :profile="profile"></profileEditor>
            </li>
            <li :class="{avctive:currentTap === 1}">
                <workEditor :workExperience="workExperience"></workEditor>
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
    import profileEditor from './profileEditor.vue'
    import workEditor from './workEditor.vue'
    export default {
        components: { profileEditor, workEditor},
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