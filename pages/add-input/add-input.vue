<template>
    <view>
        <uni-nav-bar :status-bar="true" right-text="发布" left-icon="back" @clickLeft="back" @clickRight="submit">
            <view class="nav-title" @tap="changeLook">
                {{barTitle}}
                <view class="icon iconfont icon-xialazhankai"></view>
            </view>
        </uni-nav-bar>
        <!--多行编辑-->
        <view class="uni-textarea">
            <textarea v-model="text" placeholder="说一句话吧~"></textarea>
        </view>
        <!--上传多图-->
        <upload-image @imagelist="getImageList"></upload-image>
        <!--弹出公告-->
        <!-- <button class="button" type="primary" @click="togglePopup('center', 'popup')">中间弹出 popup</button> -->
        <uni-popup ref="showtip" :type="type" :mask-click="false" @change="change">
            <view class="uni-tip">
                <image src="../../static/common/addinput.png" mode="widthFix"></image>
                <view>1、涉及黄色，政治，广告及骚扰信息</view>
                <view>2、涉及人身攻击</view>
                <view>3、留联系方式，透露他人隐私</view>
                <view>一经核实将被封禁，情节严重者永久封禁</view>
                <button class="infobtn" @click="cancel('tip')">朕知道了</button>

            </view>
        </uni-popup>
    </view>
</template>

<script>
    import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
    // import uniPopup from "@/components/uni-popup/uni-popup.vue"
    import uniSection from '@/components/uni-section/uni-section.vue'
    import uniPopup from '@/components/uni-popup/uni-popup.vue'
    import uniIcons from '@/components/uni-icons/uni-icons.vue'
    import uploadImage from "@/components/my/upload-image/upload-image.vue"

    export default {
        components: {
            uniNavBar,
            uploadImage,
            uniPopup
        },
        data() {
            return {
                looklist: ['所有人可见', '仅自己可见'],
                barTitle: "所有人可见",
                text: "",
                imageList: [],
                showpopup: true,
                type: "",
                content: "111111",
                isget:false,
            }
        },
        mounted() {
            this.togglePopup('center', 'tip');
        },
        onBackPress(){
            if(!this.text && this.imageList.length < 1){return}
            console.log(this.isget)
            if(!this.isget){
                this.saveornot();
                return true
            }
        },
        methods: {
            saveornot(){
                uni.showModal({
                    title: '提示',
                    content: '是否保存为草稿',
                    cancelText:"不保存",
                    confirmText:"保存",
                    success: (res) =>{
                        if (res.confirm) {
                          console.log("保存")
                        }else{
                            console.log("不保存")
                        }
                        this.isget = true
                        uni.navigateBack({
                            delta: 1
                        });
                    },
                });
                
            },
            back() {
                uni.navigateBack({
                    delta: 1
                });
            },
            submit() {

            },
            //修改权限
            changeLook() {
                uni.showActionSheet({
                    itemList: this.looklist,
                    success: (res) => {
                        this.barTitle = this.looklist[res.tapIndex]
                    }
                });
            },
            getImageList(arr) {
                this.imageList = arr;
            },
            hidePopup() {
                this.showpopup = false;
            },
            change() {},
            togglePopup(type, open) {
                console.log(open)
                let that = this;
                switch (type) {
                    case 'top':
                        this.content = '顶部弹出 popup'
                        break

                    case 'bottom':
                        this.content = '底部弹出 popup'
                        break
                    case 'center':
                        this.content = '居中弹出 popup'
                        break
                }
                this.type = type
                this.$nextTick(() => {
                    this.$refs['show' + open].open();
                })
            },
            cancel(type) {
                this.$refs['show' + type].close()
            },
        }
    }
</script>

<style>
    .nav-title {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .uni-textarea {
        border: 1upx solid #EEEEEE;
    }

    /* 提示窗口 */
    .uni-tip {
        /* #ifndef APP-NVUE */
        display: flex;
        flex-direction: column;
        /* #endif */
        padding: 15px;
        background-color: #fff;
        border-radius: 10px;
    }

    .uni-tip image {
        margin-bottom: 10upx;
    }

    .infobtn {
        margin-top: 20upx;
        width: 100%;
        background-color: #FFE935;
        color: #171606;
    }
</style>
