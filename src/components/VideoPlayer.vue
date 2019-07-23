<template>
    <div class="video-player">
        <div id="player" ref="player" 
            @mouseover="onMouseEvent('show')"
            @mouseleave="onMouseEvent('hide')">
            <img class="video" :src="videoImage">
            <div class="player-ui" :style="setPlayerUIDisplay">
                <div class="progress-bar">
                    <div class="playhead"></div>
                </div>
                <VideoPlayerMarker v-for="marker in videoInfo.markers" 
                    :key="marker.id"
                    :style="markerPosition(marker.timecode)"
                    :markerInfo="marker" />
                <div class="player-controls">
                    <div class="control" 
                        v-for="control in playerControls" :key="control">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import VideoPlayerMarker from '@/components/VideoPlayerMarker'
export default {
    components: {
        VideoPlayerMarker
    },
    data () {
        return {
            container: null,
            videoImage: require('../assets/images/video-image.png'),
            setPlayerUIDisplay: null,
            markerSVG: require('../assets/marker-24px.svg'),
            videoInfo: {
                duration: 547,
                markers: [
                    {
                        id: 'j3kk929c', 
                        timecode: 124, 
                        label: 'Heatwave in New York City'
                    },
                    {
                        id: 'ck39r8c2', 
                        timecode: 267, 
                        label: 'Ice Cream Trucks overwhelmed by demand, tourists'
                    },
                    {
                        id: 'q9815779', 
                        timecode: 349, 
                        label: 'Mayor escapes to Alaska, citing campaign commitments'
                    }
                ]
            },
            playerControls: [
                'control1', 'control2', 'control3'
            ],
        }
    },
    mounted () {
        this.container = this.$refs.player
    },
    methods: {
        onMouseEvent (condition) {
            condition === 'show' ? this.setPlayerUIDisplay = { display: 'block'} 
                : this.setPlayerUIDisplay = { display: 'none' }
        },
        markerPosition (timecode) {
            let calc = (100/this.videoInfo.duration) * timecode + '%'
            let position = { left: calc }
            return position
        }
    }
}
</script>
<style lang="scss" scoped>
    .video-player {
        #player {
            img {
                width: 100%;
            }
            .player-ui {
                display: none;
                .progress-bar {
                    position: relative;
                    height: 4px;
                    bottom: 45px;
                    margin: 0 10px;
                    background-color: rgba(255, 255, 255, 0.25);
                    .playhead {
                        height: 4px;
                        background-color: #fff;
                        width: 5%;
                    }
                }
            }
            .player-controls {
                display: flex;
                position: relative;
                top: -35px;
                cursor: pointer;
                .control {
                    height: 20px;
                    width: 20px;
                    margin-left: 10px;
                    background-color: #fff;
                }
            }   
        }
    }
</style>
