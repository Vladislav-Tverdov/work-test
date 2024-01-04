<template>
    <div class="lunch-list">
        <div class="lunch-list-header">
            <div :style="{ 'width': 'calc(100% - 150px)' }"><span>Бизнес-ланчи в Витебске</span></div>
            <div class="navigation-buttons-container">
                <button @click="moveLeft" class="left-arrow" :class="isMinPosition() ? 'disabled' : ''"><i></i></button>
                <button @click="moveRight" class="right-arrow"
                    :class="getMaxValidPosition() === this.currentPosition ? 'disabled' : ''"><i></i></button>
            </div>
        </div>
        <div class="scrollable-container" :style="{ 'transform': getTranslateX() }">
            <list-item v-for="item in lunchList" :item="item"></list-item>
        </div>
    </div>
</template>
<script>
import ListItem from './ListItem.vue'
export default {
    data() {
        return {
            currentPosition: 0

        }
    },
    components: {
        ListItem
    },
    props: {
        lunchList: {
            type: Array
        }
    },
    created() {
        window.addEventListener("resize", this.onResize);
    },
    unmounted() {
        window.removeEventListener("resize", this.onResize);
    },
    methods: {
        moveLeft() {
            this.currentPosition += window.innerWidth < 870 ? window.innerWidth < 500 ? 51 : 34.5 : 25;
        },
        moveRight() {
            this.currentPosition -= window.innerWidth < 870 ? window.innerWidth < 500 ? 51 : 34.5 : 25;
        },
        getTranslateX() {
            return `translateX(${this.currentPosition}%)`
        },
        getMaxValidPosition() {
            return -((this.lunchList.length - (window.innerWidth < 870 ? window.innerWidth < 500 ? 2 : 3 : 4)) * (window.innerWidth < 870 ? window.innerWidth < 500 ? 51 : 34.5 : 25));
        },
        isMinPosition() {
            return this.currentPosition === 0
        },
        onResize() {
            this.currentPosition = 0;
        }


    },

}
</script>
<style>
.scrollable-container {
    white-space: nowrap;
    -webkit-transition: -webkit-transform 0.3s;
    transition: transform 0.3s;
}

button {
    border: none;
    outline: none;
    cursor: pointer;
}

.disabled {
    opacity: 0.1;
    cursor: default;
}

i {
    width: 21px;
    height: 38px;
    display: inline-block;
    padding: 20px 21px;
}

.left-arrow {
    background: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjwhLS0gR2VuZXJhdG9yOiBBZG9iZSBJbGx1c3RyYXRvciAxOS4yLjEsIFNWRyBFeHBvcnQgUGx1Zy1JbiAuIFNWRyBWZXJzaW9uOiA2LjAwIEJ1aWxkIDApICAtLT4NCjxzdmcgdmVyc2lvbj0iMS4xIiBpZD0i0KHQu9C+0LlfMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgeD0iMHB4IiB5PSIwcHgiDQoJIHdpZHRoPSIyMXB4IiBoZWlnaHQ9IjM4cHgiIHZpZXdCb3g9IjAgMCAyMSAzOCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMjEgMzg7IiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCjxwb2x5Z29uIHBvaW50cz0iMTksMCAyMSwyIDQsMTkgMjEsMzYgMTksMzggMCwxOSAiLz4NCjwvc3ZnPg0K) no-repeat 50% 50%;
}

.right-arrow {
    background: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjwhLS0gR2VuZXJhdG9yOiBBZG9iZSBJbGx1c3RyYXRvciAxOS4yLjEsIFNWRyBFeHBvcnQgUGx1Zy1JbiAuIFNWRyBWZXJzaW9uOiA2LjAwIEJ1aWxkIDApICAtLT4NCjxzdmcgdmVyc2lvbj0iMS4xIiBpZD0i0KHQu9C+0LlfMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgeD0iMHB4IiB5PSIwcHgiDQoJIHdpZHRoPSIyMXB4IiBoZWlnaHQ9IjM4cHgiIHZpZXdCb3g9IjAgMCAyMSAzOCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMjEgMzg7IiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCjxwb2x5Z29uIHBvaW50cz0iMiwwIDAsMiAxNywxOSAwLDM2IDIsMzggMjEsMTkgIi8+DQo8L3N2Zz4NCg==) no-repeat 50% 50%;
}

.lunch-list-header {
    display: flex;
    align-items: center;
    background-color: rgb(234, 234, 215);
    padding: 22px 0 28px 18px;
    height: 60px;
}

.lunch-list-header span {
    line-height: 50px;
    border-bottom: 5px solid transparent;
    font: 900 60px/60px Roboto;
    font-size: clamp(20px, 5vw, 60px);
    letter-spacing: -1px;
    color: #000;
    cursor: pointer;
}

.lunch-list-header span:hover {
    border-color: #000;
}

.lunch-list {
    width: calc(100% - 20px);
    margin: 10px;
    min-width: 380px;
    white-space: nowrap;
    overflow: hidden;
    cursor: default;
    border-top: 1px solid #ddd;
    border-bottom: 1px solid #ddd;
    background-color: rgb(243, 227, 206);
}
</style>