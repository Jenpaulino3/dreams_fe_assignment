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
                <div class="marker"
                        v-for="marker in videoInfo.markers" 
                        :key="marker.id"
                        :style="markerPosition(marker.timecode)"
                        @mouseover="onMarkerEvent(true)"
                        @mouseleave="onMarkerEvent(false)">
                        <svg 
                            xmlns="http://www.w3.org/2000/svg" 
                            width="24" 
                            height="24" 
                            viewBox="0 0 24 24">
                                <path d="M0 0h24v24H0z" fill="none"/>
                                <path 
                                    d="M17.63 5.84C17.27 5.33 16.67 5 16 5L5 5.01C3.9 5.01 3 5.9 3 7v10c0 1.1.9 1.99 2 1.99L16 19c.67 0 1.27-.33 1.63-.84L22 12l-4.37-6.16z" 
                                    :fill="markerIsHovered ? '#00A3FF' : 
                                    '#fff' " />
                        </svg>
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
            markerSVG: require('../assets/marker-24px.svg'),
            markerIsHovered: false,
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
                : this.setPlayerUIDisplay = { display: 'block' }
        },
        markerPosition (timecode) {
            let calc = (100/this.videoInfo.duration) * timecode + 'px'
            let position = { left: calc }
            return position
        },
        onMarkerEvent (condition) {
            condition === true ? this.markerIsHovered = true 
                : this.markerIsHovered = false
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
                display: block;
                .progress-bar {
                    display: flex;
                    position: relative;
                    height: 5px;
                    top: -45px;
                    margin: 0 10px;
                    background-color: lightgrey;
                    .playhead {
                        height: 5px;
                        background-color: #fff;
                        width: 40px;
                    }
                }
                .marker {
                    position: absolute;
                    margin-top: -75px;
                    svg {
                        transform: rotate(90deg);
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
