<template>
    <div
        :id="animateId"
        :class="currentAnimateName"
        :style="{
            'animation-delay': delay + 's',
            'animation-duration': duration + 's',
        }"
    >
        <slot></slot>
    </div>
</template>

<script>
export default {
    props: {
        animateClassName: {
            type: String,
            required: true,
        },
        delay: {
            type: Number,
        },
        duration: {
            type: Number,
        },
    },
    data() {
        return {
            animate: true,
            animateId: "animate" + parseInt(Math.random() * 1e8),
        };
    },
    computed: {
        currentAnimateName() {
            return "animated " + this.animateClassName;
        },
    },

    mounted() {
        let app = document.getElementById(this.animateId);
        app.addEventListener("webkitAnimationStart", () => {
            this.$emit("animationStart");
        });
        // 动画重复运动时事件
        app.addEventListener("webkitAnimationIteration", () => {
            this.$emit("animationIteration");
        });
        app.addEventListener("webkitAnimationEnd", () => {
            this.$emit("animationEnd");
        });
    },
    destroyed() {
        let app = document.getElementById(this.animateId);
        app.removeEventListener("webkitAnimationStart");
        app.removeEventListener("webkitAnimationIteration");
        app.removeEventListener("webkitAnimationEnd");
    },
};
</script>

<style>
@import url("~@/assets/animate.css");
@import url("~@/assets/style.css");
</style>
