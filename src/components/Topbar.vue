<template>
    <div id="topbar">
        <div class="logo">
            个人简历
        </div>
        <div class="actions">
            <el-button type="primary">保存</el-button>
            <el-button>预览</el-button>
        </div>
    </div>
</template>

<style lang='scss'>
    #topbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 16px;
        box-shadow: 0 0 5px #5d5d5d;
        position: relative;
        z-index: 1;
        .logo {
            font-size: 20px;
        }
    }
</style>