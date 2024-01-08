<template>
    <div class="list-item-container">
        <div class="list-item-header" @click="openLink" :style="{ 'background-image': getImageUrl }">
            <span class="company-name">{{ item.name }}</span>
            <span class="header-text">{{ item.address }}</span>
            <span class="header-text">{{ item.lunchTime }}</span>
        </div>
        <div class="list-item-content">
            <ul class="menu-list">
                <li class="menu-item" v-for="menuItem in item.lunchMenu">
                    <span class="menu-title">{{ menuItem.name }}</span>
                    <span class="menu-price" title="Стоимость блюда">{{ getPrice(menuItem.price, false) }}</span>
                </li>
            </ul>
        </div>
        <div class="summary-price"><span>{{
            getPrice(item.summaryPrice, true)
        }}</span></div>

    </div>
</template>

<script>
export default {
    props: {
        item: {
            type: Object
        }
    },
    methods: {
        getPrice(price, withPrefix) {
            return price ? `${new Intl.NumberFormat().format(price)} ${withPrefix ? "р" : ""}` : ""
        },
        openLink() {
            window.open(`https://${this.item.url}/`, "_blank");
        }
    },
    computed: {
        getImageUrl: {
            get() {
                return `url(${this.item.image})`
            }
        },
    }
}
</script>

<style>
.list-item-container:hover>.summary-price span {
    color: white;
    background-color: red;
}

.address {
    border-bottom: 1px solid transparent;
    cursor: pointer;
}

.address:hover {
    border-color: white;
}


.summary-price span {
    font: 900 24px/29px roboto;
    margin: 5px 0px 0px 19px;
    padding: 0px 5px 2px 5px;
    border-radius: 2px;
    -webkit-transition: background-color 0.3s;
    transition: background-color 0.3s;
}

.menu-item {
    margin-bottom: 13px;
    list-style: none;
}

.menu-list {
    padding: 12px 35px 0px 23px;
}

.menu-title {
    font: 300 17px/22px roboto;
    padding: 2px 0;
}

.menu-price {
    font: 11px/16px "open sans";
    display: inline-block;
    margin: 4px 0 0 7px;
    background: #c3b8a5;
    padding: 0 3px;
    border-radius: 2px;
    vertical-align: baseline;
    position: absolute;
}

.company-name {
    font: 700 21px/23px "Roboto Condensed";
    border-bottom: 2px solid transparent;
    width: fit-content;
    text-shadow: 0 1px 0 rgba(0, 0, 0, 0.35);
    cursor: pointer;
}

.company-name:hover {
    border-color: white;
}

.list-item-container {
    width: 50%;
    border-right: 1px solid transparent;
    display: inline-block;
    vertical-align: top;
    padding: 0 0 40px 0;
    white-space: normal;
    position: relative;
}

@media screen and (min-width: 500px) {
    .list-item-container {
        width: 34.5%
    }

}

@media screen and (min-width: 850px) {
    .list-item-container {
        width: 25%
    }

}


.list-item-header {
    display: flex;
    flex-direction: column;
    height: 150px;
    color: #fff;
    background-color: #a1887f;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 50%;
    padding: 15px 38px 0 23px
}

.list-item-header:hover {
    cursor: pointer;
}

.header-text {
    margin-top: 8px;
    width: fit-content;
    cursor: default;
}
</style>