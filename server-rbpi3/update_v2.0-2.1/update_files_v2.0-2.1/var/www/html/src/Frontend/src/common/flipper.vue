<template>
    <div class="flip-container"
        :class="{flipped: flipped}">
        <div class="flipper">
            <div class="front">
                <slot name="front"></slot>
            </div>
            <div class="back">
                <slot name="back"></slot>
            </div>
        </div>
    </div>
</template>

<script>
    // https://davidwalsh.name/css-flip
    export default {
        props: ['flipped']
    };
</script>

<style lang="scss">
    .flip-container {
        perspective: 1000px;
        transform-style: preserve-3d;
        &.flipped {
            .back {
                transform: rotateY(0deg);
            }
            .front {
                transform: rotateY(180deg);
            }
        }
        &, .front, .back {
            width: 100%;
            // height of the flipper is set in square-link
            /*height: 240px;*/
        }
        .flipper {
            transition: 0.6s;
            transform-style: preserve-3d;
            position: relative;
        }
        .front, .back {
            backface-visibility: hidden;
            transition: 0.6s;
            transform-style: preserve-3d;
            position: absolute;
            top: 0;
            left: 0;
        }
        .front {
            z-index: 2;
            transform: rotateY(0deg);
        }
        .back {
            transform: rotateY(-180deg);
        }
    }
</style>
