<template>
  <v-container>
    <v-row justify="space-between" class="mb-5 pb-5 ml-2 mr-2">
      <h2>FINANCEIRO</h2>
    </v-row>
    <v-data-table
      :headers="headersTable"
      :items="financeData"
      mobile-breakpoint="0"
      item-key="_id"
      class="elevation-1"
    >
      <template v-slot:item.paymentStatus="{ item }">
        <div
          :class="item.paymentStatus ? 'success--text' : 'red--text'"
        >{{ item.paymentStatus ? 'Recebido' : 'Pendente'}}</div>
      </template>

      <template v-slot:item.payment="{ item }">
        <v-btn
          @click="item.paymentStatus = !item.paymentStatus, takePaymentStatus(item)"
          class="text-capitalize ma-3"
          :color="item.paymentStatus ? 'error' : 'success'"
        >{{ item.paymentStatus ? 'Cancelar pagamento' : 'Confirmar pagamento'}}</v-btn>
      </template>

      <template v-slot:body.append>
        <tr style="background-color:#f5f5f5">
          <td></td>
          <td></td>
          <td></td>
          <td class="font-weight-medium">Total</td>
          <td
            class="success--text font-weight-medium"
          >{{ formatValue(financeData.reduce((acc, { total, paymentStatus }) => acc + parseFloat(`${paymentStatus ? parseFloat(total.replace('R$', '')) : 0}`), 0)) }}</td>
        </tr>
      </template>
    </v-data-table>
  </v-container>
</template>

<script src="./script.js" />