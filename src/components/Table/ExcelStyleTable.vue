<script setup>
import { ref } from "vue";

const rows = ref([1]);
const columns = ref([1]);
const inputValue = "";

const addRow = () => {
  rows.value.push(inputValue.value);
};

const deleteRow = () => {
  rows.value.pop();
};

const addColumn = () => {
  columns.value.push(inputValue.value);
};

const removeColumn = () => {
  columns.value.pop();
};

const removeAll = (index) => {
  rows.value.splice(index, rows.value.length);
  columns.value.splice(index, columns.value.length);

  rows.value.push(1);
  columns.value.push(1);
};
</script>

<template>
  <div class="w-full flex-col flex justify-center items-center space-y-3 py-4">
    <div class="flex justify-center space-x-6">
      <button
        @click="addRow"
        class="px-2 py-2 text-sm font-semibold rounded-full bg-sky-400"
      >
        +1 row
      </button>
      <button
        @click="deleteRow"
        class="px-2 py-2 text-sm font-semibold rounded-full bg-sky-400"
      >
        -1 row
      </button>
      <button
        @click="addColumn"
        class="px-2 py-2 text-sm font-semibold rounded-full bg-sky-400"
      >
        +1 column
      </button>
      <button
        @click="removeColumn"
        class="px-2 py-2 text-sm font-semibold rounded-full bg-sky-400"
      >
        -1 column
      </button>

      <button
        @click="removeAll(index)"
        class="px-2 py-2 text-sm font-semibold rounded-full bg-sky-400"
      >
        Delete All
      </button>
    </div>
    <div
      class="flex flex-col space-y-2 max-w-7xl max-h-[80vh] overflow-x-auto overscroll-x-contain p-3"
    >
      <table class="">
        <thead></thead>
        <tbody>
          <tr class="" v-for="(row, index) in rows" :key="index">
            <td class="border border-slate-600" v-for="column in columns">
              <input
                type="text"
                class="h-auto border-none focus:outline-none text-sm font-semibold px-1"
                v-model="inputValue"
              />
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
