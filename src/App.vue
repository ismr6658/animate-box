<template>
    <div id="app">
        <animate-box
            @animationStart="animationStart"
            @animationIteration="animationIteration"
            @animationEnd="animationEnd"
            animateClassName="fadeInLeft"
            ><div class="_animation-box">{{ str }}</div></animate-box
        >
        <animate-box
            animateClassName="fadeInLeft"
            class="_animation-box"
            :delay="0.6"
            >fadeInLeft</animate-box
        >
    </div>
</template>

<script>
import animateBox from "./components/animateBox.vue";

export default {
    components: {
        animateBox,
    },
    data() {
        return {
            str: null,
        };
    },
    methods: {
        animationStart() {
            this.str = "动画开始";
            console.log("动画开始");
        },
        animationIteration() {
            console.log("动画重复中");
        },
        animationEnd() {
            this.str = "动画结束";
            console.log("动画结束");
        },
    },
};
</script>

<style>
._animation-box {
    width: 310px;
    height: 200px;
    background: skyblue;
    margin: 20px;
}

.top-line {
    position: absolute;
    height: 100%;
    left: 0;
    animation: topRunLight 2.5s linear infinite;
}

@keyframes topRunLight {
    0% {
        left: 0;
        opacity: 0.6;
    }

    50% {
        left: 50%;
        opacity: 1;
    }

    100% {
        left: 100%;
        opacity: 0;
    }
}
</style>
