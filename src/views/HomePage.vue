<template>
    <div class="homepage">
        <VideoPlayer />
    </div>
</template>
<script>
import VideoPlayer from '@/components/VideoPlayer'
export default {
    components: {
        VideoPlayer
    }
}
</script>
<style lang="scss" scoped>
    .homepage {
        #player {
            img {
                width: 100%;
            }
        }
    }
</style>
