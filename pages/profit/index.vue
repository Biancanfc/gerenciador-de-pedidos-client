<template>
  <v-container>
    <v-row justify="space-between" class="mb-5 pb-5 ml-2 mr-2">
      <h2>FINANCEIRO</h2>
    </v-row>
    <v-simple-table class="pa-5" style="margin-bottom:50px; border:1px solid #f5f5f5">
      <template v-slot:default>
        <thead>
          <h2>Rendimento com base nos recebimentos</h2>
        </thead>
        <tbody>
          <tr v-for="(item, i) in tableFinanceProfit" :key="i">
            <td>{{ item.description }}</td>
            <td>{{ formatValue(item.total) }}</td>
          </tr>
          <tr
            :style="`${ totalFinance - totalCost < 0  ? 'background-color:#ff000020' : 'background-color: #00ff0020'}`"
          >
            <td>Total</td>
            <td>{{ formatValue(totalFinance - totalCost) }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
    <v-simple-table class="pa-5" style="margin-bottom:50px; border:1px solid #f5f5f5">
      <template v-slot:default>
        <thead>
          <h2>Rendimento com base na receita</h2>
        </thead>
        <tbody>
          <tr v-for="(item, i) in tableRecipeProfit" :key="i">
            <td>{{ item.description }}</td>
            <td>{{ formatValue(item.total) }}</td>
          </tr>
          <tr
            :style="`${ totalRecipe - totalCost < 0  ? 'background-color:#ff000020' : 'background-color: #00ff0020'}`"
          >
            <td>Total</td>
            <td>{{ formatValue(totalRecipe - totalCost) }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </v-container>
</template>

<script src="./script.js" />