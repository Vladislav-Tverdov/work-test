<template>
    <div>
        <lunch-list :lunchList="lunchList"></lunch-list>
    </div>
</template>
<script>
import LunchList from './Components/ListWithHorizontalScrolling.vue'
export default {
    components: {
        LunchList
    },
    data() {
        return {
            lunchList: [
                {
                    name: "Ностальгия",
                    image: "https://carte.by/source/photos/2020/03/11/c9fbfc8f431eab848379ad1b8b70b571_p.jpg",
                    url: "nostalgia.vitebsk.biz",
                    address: "Витебск, пр-т Московский,86", // можно сделать составным {city:"",street:"",house/flat:""} если есть форма заполнения
                    lunchTime: "12:00-16:00",// можно тоже сделать составным при наличии формы заполнения {startTime:number,endTime:number}
                    lunchMenu: [
                        {
                            name: "Суп «Рисовый» с грибами",
                            price: null
                        },
                        {
                            name: "Котлета «Несвиж», пюре картофельное",
                            price: null
                        },
                        {
                            name: "Салат «Белоснежка»",
                            price: null
                        },
                    ],
                    summaryPrice: 9.95
                },
                {
                    name: "Губернский трактир",
                    image: "https://carte.by/source/photos/2017/06/22/dsc-9035_p.jpg",
                    url: "gubernskiy.vitebsk.biz",
                    address: "Витебск, ул. Комсомольская, 11/5",
                    lunchTime: "12:00-15:00",
                    lunchMenu: [
                        {
                            name: "Салат «Слоёный»",
                            price: 1.65
                        },
                        {
                            name: "Щи со свежей капустой, сметаной и хлебом",
                            price: 3.70
                        },
                        {
                            name: "Азу из говядины, картофельное пюре»",
                            price: 7.20
                        },
                    ],
                    summaryPrice: 12.55
                },
                {
                    name: "Город",
                    image: "https://carte.by/source/photos/2017/03/22/gorod_p.jpg",
                    url: "gorod.vitebsk.biz",
                    address: "Витебск, ул. Смоленская, 3/1",
                    lunchTime: "",
                    lunchMenu: [
                        {
                            name: "Птица заливная с хреном",
                            price: 3.70
                        },
                        {
                            name: "Борщ «Украинский» с пампушками",
                            price: 2.80
                        },
                        {
                            name: "Котлета «Киевская», картофельное пюре с морковью «По-корейски»",
                            price: 5.70
                        },
                    ],
                    summaryPrice: 12.20
                },
                {
                    name: "Лямус",
                    image: "https://carte.by/source/photos/2015/11/30/liamus_p.jpg",
                    url: "liamus.vitebsk.biz",
                    address: "Витебск, пр-т Победы, 1",
                    lunchTime: "12:00-16:00",
                    lunchMenu: [
                        {
                            name: "Салат из свёклы с фруктами",
                            price: 3.50
                        },
                        {
                            name: "Супчик куриный с рисом",
                            price: 4.50
                        },
                        {
                            name: "Котлета «По-домашнему», картофельное пюре с маринованной капустой",
                            price: 8.00
                        },
                    ],
                    summaryPrice: 16
                },
                {
                    name: "Pizza Smile",
                    image: "https://cdn.carte.by/assets/2023/02/06/f7ab7b1265c861f02fd4684c254de5---png_700x385:center:whitepadding15_6baba_convert.webp",
                    url: "pizzasmile.vitebsk.biz",
                    address: "Витебск, ул. Чкалова, 35",
                    lunchTime: "12:00-15:00",
                    lunchMenu: [
                        {
                            name: "Салат «Весенний»",
                            price: null
                        },
                        {
                            name: "Суп грибной с перловой крупой",
                            price: null
                        },
                        {
                            name: "Котлета рубленая из птицы со сливочным соусом, картофель отварной",
                            price: null
                        },
                    ],
                    summaryPrice: 7
                },
            ]
        }
    }
}
</script>
<style></style>