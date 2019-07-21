<template>
    <div class="video-player">
        <div id="player">
            <img class="video" :src="require('../assets/images/video-image.png')">
        </div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss" scoped>
    .video-player {
        #player {
            img {
                width: 100%;
            }
        }
    }
</style>
