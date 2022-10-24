<script setup>
import Input from "./Input.vue";
import { ref, computed } from "vue";
import SectionCard from "./SectionCard.vue";
import Button from "./Button.vue";

const props = defineProps({
  heading: {
    type: String,
  },
});

const open = ref(false);

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

//eftpos values
const totalCard = ref(0);
const amexSales = ref(0);
const cardsMinusAmex = computed(() => {
  return totalCard.value - amexSales.value;
});

const NotesTotal = computed(() => {
  let sum =
    parseInt(hundreds.value) +
    parseInt(fifties.value) +
    parseInt(twenties.value) +
    parseInt(tens.value) +
    parseInt(fives.value);
  return sum;
});

const CoinsTotal = computed(() => {
  let sum =
    parseInt(coinsTwo.value) +
    parseInt(coinsOne.value) +
    parseInt(coinsFifty.value) +
    parseInt(coinsTwenty.value) +
    parseInt(coinsTen.value) +
    parseInt(coinsFive.value);
  return sum;
});

function saveTill() {
  console.log({
    notes: {
      100: hundreds.value,
      50: fifties.value,
      20: twenties.value,
      10: tens.value,
      5: fives.value,
    },
    coins: {
      2: coinsTwo.value,
      1: coinsOne.value,
      50: coinsFifty.value,
      20: coinsTwenty.value,
      10: coinsTen.value,
      5: coinsFive.value,
    },
    eftpos: {
      amex: amexSales.value,
      total: cardsMinusAmex.value,
    },
  });
}
</script>

<template>
  <div v-if="open">
    <SectionCard>
      <div class="grid grid-cols-3 max-w-4xl">
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
        <div>
          <h2 class="font-medium my-2">Cards</h2>
          <Input label="Amex sales" v-model="amexSales"></Input>
          <Input label="Total Eftpos" v-model="totalCard"></Input>
        </div>
      </div>
      <div>Notes total: ${{ NotesTotal }}</div>
      <div>Coins Total: ${{ CoinsTotal }}</div>
      <template #footer>
        <Button class="mr-4">Clear</Button>
        <Button @click="saveTill">Save</Button>
      </template>
    </SectionCard>
    <SectionCard>
      <div class="flex justify-end">
        <Button @click="open = true"> + Add Till</Button>
      </div>
      <template #footer> </template>
    </SectionCard>
  </div>
  <SectionCard v-else>
    <div class="flex justify-end">
      <Button @click="open = true"> + Add Till</Button>
    </div>
    <template #footer> </template>
  </SectionCard>
</template>
