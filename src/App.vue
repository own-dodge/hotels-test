<template>
    <div class="header">
        <div class="header_left">
            <a href="#" class="header_burger"><svg class="icon24">
                    <use xlink:href="#"></use>
                </svg></a>
            <div class="header_logo active">
                <a class="logo" href="#">T<span>op</span> C<span>lient</span></a>
                <div class="side_toggle">
                    <a href="#">
                        <svg class="icon24">
                            <use xlink:href="#"></use>
                        </svg>
                    </a>
                </div>
            </div>
            <div class="header_cent">
                <a href="#">Справочный Центр<span>Помощь</span></a>
            </div>
            <div class="header_tech">
                <a href="tel:88006008013">8 (800) 600 80 13</a>
                <a href="mailto:hd@clubwings.ru">hd@clubwings.ru</a>
            </div>
        </div>
        <div class="header_right">
            <div class="header_ico">
                <div class="header_currency">
                    <a href="#"><svg class="icon24 icon_rus icon_bord">
                            <use xlink:href="#"></use>
                        </svg>RU</a>
                    <a href="#"><svg class="icon24 icon_fill">
                            <use xlink:href="#"></use>
                        </svg>USD</a>
                </div>
                <div class="header_user_mess">
                    <a href="#"><svg class="icon24">
                            <use xlink:href="#"></use>
                        </svg></a>
                </div>
            </div>
            <div class="header_user">
                <a href="#"><span>Ольга Кузьма</span> <img alt="profile_img" src="img/profile_img.png" width="40"
                        height="40"></a>
            </div>
        </div>
    </div>
    <div class="work_area">
        <div class="sidebar active">
            <div class="group_block">
                <div class="side_logo">
                    <a href="#"><img alt="side_logo" src="img/side_logo.svg" width="50" height="50"></a>
                    <div class="side_plane">
                        <div class="plane_name">Travel plane</div>
                        <div class="plane_price">540 000 ₽</div>
                    </div>
                </div>
            </div>
            <div class="group_block">
                <ul class="side_nav">
                    <li class="active"><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Главная</a></li>
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Услуги</a></li>
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Заказы</a></li>
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Статистика</a></li>
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Компании</a></li>
                </ul>
            </div>
            <div class="group_block">
                <ul class="side_nav">
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Новости</a></li>
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Настройки</a></li>
                </ul>
            </div>
            <div class="group_block">
                <ul class="side_nav">
                    <li><a href="#"><svg class="icon24">
                                <use xlink:href="#" />
                            </svg>Выйти</a></li>
                </ul>
            </div>
        </div>
        <div class="wrapper">

            <div style="height: 900px;"></div>

            <div class="modal_side modal_right" style="display: block;">
                <div class="modal_side_wrap">
                    <div class="modal_head modal_head_tarif">
                        <h5>Правила тарифа</h5>
                        <div class="tarif_switch tabs tabs-but">
                            <a v-for="pax in paxSegment" @click="changeSegment" href="#" class="swit_tarif1" :class="(activeIndex === pax.PaxSegmentID) ? 'active' : ''"
                                :id="pax.PaxSegmentID" :key="pax.PaxSegmentID">
                                {{ pax.Dep.IATA_LocationCode }} - {{ pax.Arrival.IATA_LocationCode }}
                            </a>
                        </div>
                        <div class="razdel_switch tabs tabs-but">
                            <a href="#" class="swit_razdel1 active">Раздел 15</a>
                            <a href="#" class="swit_razdel2">Раздел 16</a>
                            <a href="#" class="swit_razdel3">Раздел 21</a>
                            <a href="#" class="swit_razdel4">Раздел 22</a>
                        </div>
                        <a href="#" class="btn btn-icon btn-blue_fill modal_close">
                            <svg class="icon18">
                                <use xlink:href="#"></use>
                            </svg>
                        </a>
                    </div>
                    <div class="rules_wrap">
                        <div class="rules_item">
                            <span v-html="rulesText"></span>
                        </div>
                    </div>
            </div>
        </div>
        <div class="lay" style="display: block"></div>

    </div>
</div></template>

<script>
import rulesData from "@/rules.json";
console.log(rulesData)

export default {
    name: 'App',
    data() {
        return {
            paxSegment: rulesData.DataLists.PaxSegmentList.PaxSegment,
            rulesText: null,
            idPax: null,
            activeIndex: null,
        }
    },
    methods: {
        changeSegment(e) {
            this.idPax = e.currentTarget.id;
            this.rulesText = rulesData.Rules.find((el) => el.PaxSegmentRefID === this.idPax).FareRuleText.Remark.RemarkText;
            this.activeIndex = (this.activeIndex === e.currentTarget.id) ? null : e.currentTarget.id;
        },
    }
}
</script>
