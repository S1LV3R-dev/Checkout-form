<script setup>
import { ref, watch } from 'vue';
const name = ref("");
const value = ref("");
const mask = "####-####-####-####";
const month = ref();
const year = ref();
const card_num = ref(mask);
const props = defineProps(['price']);
const price = props['price'];
watch(month, (newValue, oldValue) => {
    console.log(newValue, oldValue)
    if (newValue != '') {
        if (newValue > 12) {
            month.value = 12;
        } else if (newValue >= 10) {
            if (newValue.toString()[0] === '0') {
                month.value = newValue.replace('0', '');
            }
        } else if (newValue < 10 && newValue > 0) {
            month.value = ('0' + month.value).slice(-2);
        } else if (newValue == '0') {
            month.value = '';
        } else if (newValue < 0) {
            month.value = 1;
        }
    }
});
watch(year, (newValue, oldValue) => {
    console.log(newValue, oldValue)
    if (newValue != '') {
        if (newValue >= 10) {
            if (newValue.toString()[0] === '0') {
                year.value = newValue.replace('0', '');
            }
        } else if (newValue < 10 && newValue > 0) {
            year.value = ('0' + year.value).slice(-2);
        } else if (newValue == '0') {
            year.value = '';
        } else if (newValue < 0) {
            year.value = 1;
        }
    }
});

</script>

<template>
    <div id="card_info_block">
        <form id="card_info">
            <h3>Payment information</h3>
            <div id="card">
                <div id="chip_img">
                    <img src='../assets/chip.svg' height="50px" />
                </div>
                <span id="card_number"> {{ card_num }}</span>
                <div id="card_bottom">
                    <div id="card_bottom_left">
                        <div class="card_label">
                            Card holder
                        </div>
                        <span>
                            {{ name.toUpperCase() || "FULL NAME" }}
                        </span>
                    </div>
                    <div id="card_bottom_right">
                        <div class="card_label">
                            Expires
                        </div>
                        {{ month || "MM" }}/{{ year || "YY" }}
                    </div>
                </div>
            </div>
            <div id="card_info_input">
                <span class="card_info_label">Name on card</span>
                <input type="text" class="card-info-input-field" v-model="name" />

                <span class="card_info_label">Card number</span>
                <input type="text" class="card-info-input-field" @input="card_num = value + mask.slice(value.length)"
                    v-mask="mask" v-model="value" />
                <div id="card_info_bottom">
                    <div id="card_info_expiration_date">
                        <span class="card_info_label">Expiration date</span>
                        <div id="card_info_inputs">
                            <input class="card-info-input-field small-input-field" id="month" type="text" v-mask="'##'"
                                @input="minmax" v-model="month" placeholder="Month" />
                            <input class="card-info-input-field small-input-field" id="year" type="text" v-mask="'##'"
                                v-model="year" placeholder="Year" />
                        </div>
                    </div>
                    <div id="cvc">
                        <span class="card_info_label">CVC</span>
                        <div>
                            <input class="card-info-input-field small-input-field" id="cvc_input" type="text"
                                mask="'###'" />
                        </div>
                    </div>
                </div>
            </div>
            <div id="price_tag">
                {{ price }} USD
            </div>
            <div id="confirm">
                <button>Confirm payment</button>
            </div>
        </form>
    </div>
</template>

<style></style>