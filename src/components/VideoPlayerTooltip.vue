<template>
    <div class="tooltip">
        <p>{{markerInfo.label}}</p>
    </div>
</template>
<script>
export default {
    props: {
        markerInfo: Object
    }
}
</script>
<style lang="scss" scoped>
    .tooltip {
        position: absolute;
        bottom: 85px;
        width: 275px;
        background: #fff;
        color: #000;
        border: 2px solid #00A3FF;
        border-radius: 5px;
        font-family: sans-serif;
        font-weight: bold;
        line-height: 20px;
        p {
            margin: 10px;
        }
    }
</style>
