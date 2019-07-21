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
                <div class="player-controls">
                    <div class="control" v-for="control in playerControls" :key="control">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data () {
        return {
            container: null,
            videoImage: require('../assets/images/video-image.png'),
            setPlayerUIDisplay: null,
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
    methods: {
        onMouseEvent(condition){
            condition === 'show' ? this.setPlayerUIDisplay = { display: 'block'} 
                : this.setPlayerUIDisplay = { display: 'none' }
        }
    },
    mounted () {
        this.container = this.$refs.player
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
                    height: 5px;
                    top: -45px;
                    margin: 0 10px;
                    background-color: grey;
                    // width: 547px;
                    .playhead {
                        height: 5px;
                        background-color: #fff;
                        width: 40px;
                    }
                }
            }
            .player-controls {
                display: flex;
                position: relative;
                top: -35px;
                // margin-right: 10px;
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
