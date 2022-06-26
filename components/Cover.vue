<style scoped>
    @import url("@/static/css/cover.css");
</style>
<template>
    <div class="container-fluid w-100 h-100 px-0">
        <div class="position-relative" id="cover">
            <div id="cover_overlay" class="w-100" ref="cover_overlay_ref">
                <div class="row w-100 py-3" id="cover_topbar"></div>
                <div class="container mt-5" id="cover_content">
                    <div class="row w-100 h-100 m-0 p-0 justify-content-center">
                        <div class="col-md-12">
                            <div class="text-center">
                                <span class="subheading slide" ref="subheading_ref">The Wedding Of</span>
                                <h3 id="bride_name" class="mt-4 slide" ref="bride_name_ref">
                                    <p class="d-none d-md-block">Wawan & Dheta</p>
                                    <p class="mb-0 d-block d-md-none">Wawan</p>
                                    <p class="mb-0 d-block d-md-none">&</p>
                                    <p class="mb-0 d-block d-md-none">Dheta</p>
                                </h3>
                            </div>
                            <div ref="cover_date_ref" class="slide">
                                <p class="countdown">
                                    {{ wedding_real_date }}
                                </p>
                            </div>
                            <client-only>
                                <VueCountdown :time="wedding_date.getTime() - now.getTime()">
                                    <template slot-scope="props">
                                        <div class="container-fluid mt-4 slide" ref="cover_countdown_ref">   
                                            <div class="d-flex justify-content-center">
                                                <div class="countdown">
                                                    <p>{{ props.days }}</p>
                                                    <p>Hari</p>
                                                </div>
                                                <div class="countdown">
                                                    <p>{{ props.hours }}</p>
                                                    <p>Jam</p>
                                                </div>
                                                <div class="countdown">
                                                    <p>{{ props.minutes }}</p>
                                                    <p>Menit</p>
                                                </div>
                                                <div class="countdown">
                                                    <p>{{ props.seconds }}</p>
                                                    <p>Detik</p>
                                                </div>
                                            </div>
                                        </div>
                                    </template>
                                </VueCountdown>
                            </client-only>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import VueCountdown from '@chenfengyuan/vue-countdown';
export default {
    data() {
        return {
            wedding_date: new Date(2022, 8, 18, 9, 0, 0),
            now: new Date(),
            wedding_real_date: 'Minggu, 18 September 2022',
            old_scroll: 0
        }
    },
    mounted() {
        this.initCover()
        this.disableParallaxIfIsSafari()
    },
    methods: {
        disableParallaxIfIsSafari() {
            var isSafari = /constructor/i.test(window.HTMLElement) || (function (p) { return p.toString() === "[object SafariRemoteNotification]"; })(!window['safari'] || (typeof safari !== 'undefined' && window['safari'].pushNotification));
            if(isSafari) {
                document.getElementById('cover_overlay').style.backgroundAttachment = 'none'
            }
        },
        initCover() {
            this.$refs.subheading_ref.classList.add('slide-up')
            setTimeout(() => {
                this.$refs.bride_name_ref.classList.add('slide-up')
                this.$refs.cover_date_ref.classList.add('slide-up')
                this.$refs.cover_countdown_ref.classList.add('slide-up')
            }, 400)
        }
    },
    components: {
        VueCountdown
    }
}
</script>