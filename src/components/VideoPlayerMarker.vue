<template>
    <div>
        <div class="marker"
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
    </div>
</template>
<script>
export default {
    data () {
        return {
            markerIsHovered: false
        }
    },
    methods: {
        onMarkerEvent (condition) {
            condition === true ? this.markerIsHovered = true 
                : this.markerIsHovered = false
        }
    }
}
</script>
<style lang="scss" scoped>
    div {
        display: flex;
        position: relative;
        .marker {
            position: absolute;
            margin-top: -75px;
            cursor: pointer;
            svg {
                transform: rotate(90deg);
            }
        }
    }
</style>