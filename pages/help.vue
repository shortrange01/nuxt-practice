<template>
    <div class="help bg-red-300">
        <div>
            <div id="trigger1" class="trigger1 bg-blue-500"></div>
            <div
                id="trigger2"
                class="trigger2 border-8 opacity-50 bg-gray-400"
            ></div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
export default Vue.extend({
    mounted() {
        // eslint-disable-next-line no-console
        console.info(gsap)
        this.scrollItemA()
        this.scrollItemB()
    },
    beforeDestroy() {
        // 遷移時インスタンス削除
        ScrollTrigger.getAll().map((target) => {
            target.kill(true)
        })
    },
    methods: {
        scrollItemA() {
            // eslint-disable-next-line no-console
            console.info(gsap)
            gsap.to('#trigger1', {
                // 動かしたい要素は"#trigger1"
                x: 300, // 右方向に500動く
                duration: 1, // アニメーションは1秒間
                scrollTrigger: {
                    trigger: '#trigger1', // 要素"#trigger1"がビューポートに入ったときにアニメーション開始
                    // start: 'center center', // アニメーション開始位置
                    start: 'top center', // アニメーション開始位置
                    end: 'top 300px', // アニメーション終了位置
                    scrub: true, // アニメーションをスクロール位置にリンクさせる
                    markers: true, // マーカー表示
                },
            })
        },
        scrollItemB() {
            const tl = gsap.timeline({
                scrollTrigger: {
                    trigger: '#trigger2', // トリガーとなる要素は"#trigger2"

                    // スクローラの中央の位置が起点(50%)
                    // トリガー要素.wrpperの中央に来たら発火(center)
                    start: 'center 50%',

                    // スクローラの頂点が上から25%の位置が起点(25%)
                    // トリガー要素.wrpperの中央に来たら終了(center)
                    end: 'center 25%',
                    scrub: true,
                    markers: true,
                },
            })
            tl.to('#trigger2', { y: 100, scale: 0.5 })
            tl.to('#trigger2', { x: 160, scale: 1 })
        },
    },
})
</script>

<style scoped>
.help {
    position: relative;
    overflow-x: hidden;
    height: 3000px;
}
.trigger1,
.trigger2 {
    position: absolute;
    width: 200px;
    height: 200px;
}

.trigger1 {
    top: 1600px;
    left: -200px;
}

.trigger2 {
    top: 1300px;
    right: 0;
    left: 0;
}
</style>
