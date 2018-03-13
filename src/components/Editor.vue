<template>
    <div id="editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]" :class="{avctive:currentTap === i}" v-on:click="currentTap = i">
                    <svg class="icon">
                        <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
                    </svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li :class="{avctive:currentTap === 0}">tab1</li>
            <li :class="{avctive:currentTap === 1}">tab2</li>
            <li :class="{avctive:currentTap === 2}">tab3</li>
            <li :class="{avctive:currentTap === 3}">tab4</li>
            <li :class="{avctive:currentTap === 4}">tab5</li>
            <li :class="{avctive:currentTap === 5}">tab6</li>
        </ol>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                currentTap: 0,
                icons: ['identity', 'experience', 'book', 'project', 'prize', 'phone']
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
            >li {
                display: none;
                &.avctive {
                    display: block;
                }
            }
        }
    }
</style>