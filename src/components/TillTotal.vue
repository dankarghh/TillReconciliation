<script setup>
import Input from "./Input.vue";
import { ref, computed } from "vue";
import SectionCard from "./SectionCard.vue";

const pros = defineProps({
  heading: {
    type: String,
  },
  //   hundreds: Number,
  //   fifties: Number,
  //   twenties: Number,
  //   tens: Number,
  //   fives: Number,
});

//note values
const hundreds = ref(0);
const fifties = ref(0);
const twenties = ref(0);
const tens = ref(0);
const fives = ref(0);

//coin values
const coinsTwo = ref(0);
const coinsOne = ref(0);
const coinsFifty = ref(0);
const coinsTwenty = ref(0);
const coinsTen = ref(0);
const coinsFive = ref(0);

const tillOneNotesTotal = computed(() => {
  let sum =
    parseInt(hundreds.value) +
    parseInt(fifties.value) +
    parseInt(twenties.value) +
    parseInt(tens.value) +
    parseInt(fives.value);
  return sum;
});

const tillOneCoinsTotal = computed(() => {
  let sum =
    parseInt(coinsTwo.value) +
    parseInt(coinsOne.value) +
    parseInt(coinsFifty.value) +
    parseInt(coinsTwenty.value) +
    parseInt(coinsTen.value) +
    parseInt(coinsFive.value);
  return sum;
});
</script>

<template>
  <SectionCard>
    <div class="grid grid-cols-2">
      <div>
        <h2>{{ heading }}</h2>
        <div>
          <h2 class="font-medium my-2">Notes</h2>
          <Input
            step="100"
            name="hundreds"
            type="number"
            v-model="hundreds"
            label="$100"
          />
          <Input
            step="50"
            name="fifties"
            type="number"
            v-model="fifties"
            label="$50"
          />
          <Input
            step="20"
            name="twenties"
            type="number"
            v-model="twenties"
            label="$20"
          />
          <Input
            step="10"
            name="tens"
            type="number"
            v-model="tens"
            label="$10"
          />
          <Input
            step="5"
            name="fives"
            type="number"
            v-model="fives"
            label="$5"
          />
        </div>
        <div>
          <h2 class="font-medium my-2">Coins</h2>
          <Input name="coinsTwo" type="number" v-model="coinsTwo" label="$2" />
          <Input name="coinsOne" type="number" v-model="coinsOne" label="$1" />
          <Input
            name="coinsFifty"
            type="number"
            v-model="coinsFifty"
            label="50c"
          />
          <Input
            name="coinsTwenty"
            type="number"
            v-model="coinsTwenty"
            label="20c"
          />
          <Input name="coinsTen" type="number" v-model="coinsTen" label="10c" />
          <Input
            name="coinsFive"
            type="number"
            v-model="coinsFive"
            label="5c"
          />
        </div>
      </div>
      <div>
        <h2>{{ heading }}</h2>
        <div>
          <h2 class="font-medium my-2">Notes</h2>
          <Input
            step="100"
            name="hundreds"
            type="number"
            v-model="hundreds"
            label="$100"
          />
          <Input name="fifties" type="number" v-model="fifties" label="$50" />
          <Input name="twenties" type="number" v-model="twenties" label="$20" />
          <Input name="tens" type="number" v-model="tens" label="$10" />
          <Input name="fives" type="number" v-model="fives" label="$5" />
        </div>
        <div>
          <h2 class="font-medium my-2">Coins</h2>
          <Input name="coinsTwo" type="number" v-model="coinsTwo" label="$2" />
          <Input name="coinsOne" type="number" v-model="coinsOne" label="$1" />
          <Input
            name="coinsFifty"
            type="number"
            v-model="coinsFifty"
            label="50c"
          />
          <Input
            name="coinsTwenty"
            type="number"
            v-model="coinsTwenty"
            label="20c"
          />
          <Input name="coinsTen" type="number" v-model="coinsTen" label="10c" />
          <Input
            name="coinsFive"
            type="number"
            v-model="coinsFive"
            label="5c"
          />
        </div>
      </div>
    </div>
    <div>Notes total: ${{ tillOneNotesTotal }}</div>
    <div>Coins Total: ${{ tillOneCoinsTotal }}</div>
  </SectionCard>
</template>
