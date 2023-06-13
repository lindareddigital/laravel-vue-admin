<script setup>
import { Head } from '@inertiajs/vue3'
import { computed, ref, onMounted } from 'vue'
import { useMainStore } from '@/Stores/main'
import {
  mdiAccountMultiple,
  mdiCartOutline,
  mdiChartTimelineVariant,
  mdiFinance,
  mdiMonitorCellphone,
  mdiReload,
  mdiGithub,
  mdiChartPie
} from '@mdi/js'
import * as chartConfig from '@/Components/Charts/chart.config.js'
import LineChart from '@/Components/Charts/LineChart.vue'
import SectionMain from '@/Components/SectionMain.vue'
import CardBoxWidget from '@/Components/CardBoxWidget.vue'
import CardBox from '@/Components/CardBox.vue'
import TableSampleClients from '@/Components/TableSampleClients.vue'
import TableRoles from '@/Components/Tables/TableRoles.vue'
import TableAvators from '@/Components/Tables/TableAvators.vue'
import TableMissions from '@/Components/Tables/TableMissions.vue'
import TableRewards from '@/Components/Tables/TableRewards.vue'
import TableUserMissions from '@/Components/Tables/TableUserMissions.vue'
import TableRewardsAudit from '@/Components/Tables/TableRewardsAudit.vue'




import NotificationBar from '@/Components/NotificationBar.vue'
import BaseButton from '@/Components/BaseButton.vue'
import CardBoxTransaction from '@/Components/CardBoxTransaction.vue'
import CardBoxClient from '@/Components/CardBoxClient.vue'
import LayoutAuthenticated from '@/Layouts/LayoutAuthenticated.vue'
import SectionTitleLineWithButton from '@/Components/SectionTitleLineWithButton.vue'
import SectionBannerStarOnGitHub from '@/Components/SectionBannerStarOnGitHub.vue'
const chartData = ref(null)
const fillChartData = () => {
  chartData.value = chartConfig.sampleChartData()
}
onMounted(() => {
  fillChartData()
})
const mainStore = useMainStore()

/* Fetch sample data */
mainStore.fetch('clients')
mainStore.fetch('history')

const clientBarItems = computed(() => mainStore.clients.slice(0, 4))
const transactionBarItems = computed(() => mainStore.history)
</script>

<template>
  <LayoutAuthenticated>
    <Head title="Dashboard" />
    <SectionMain>






      <SectionTitleLineWithButton
        :icon="mdiChartTimelineVariant"
        title="Overview"
        main
      >
        <BaseButton
          href="https://github.com/balajidharma/laravel-vue-admin-panel"
          target="_blank"
          :icon="mdiGithub"
          label="Star on GitHub"
          color="contrast"
          rounded-full
          small
        />
      </SectionTitleLineWithButton>


      <SectionTitleLineWithButton
        :icon="mdiAccountMultiple"
        title="Clients"
      />

      <NotificationBar
        color="info"
        :icon="mdiMonitorCellphone"
      >
        <b>NotificationBar</b> Collapses on mobile
      </NotificationBar>

      <CardBox
        :icon="mdiMonitorCellphone"
        title="Users"
        has-table
      >
        <TableSampleClients />

      </CardBox>


      <CardBox
        :icon="mdiMonitorCellphone"
        title="Roles"
        has-table
      >
        <TableRoles />

      </CardBox>

      <CardBox
        :icon="mdiMonitorCellphone"
        title="Avators"
        has-table
      >
        <TableAvators />

      </CardBox>


      <CardBox
        :icon="mdiMonitorCellphone"
        title="Missions"
        has-table
      >
        <TableMissions />

      </CardBox>


      <CardBox
        :icon="mdiMonitorCellphone"
        title="Rewards"
        has-table
      >
        <TableRewards />

      </CardBox>


      <CardBox
        :icon="mdiMonitorCellphone"
        title="Reward_Audit"
        has-table
      >
        <TableRewardsAudit />

      </CardBox>


      <CardBox
        :icon="mdiMonitorCellphone"
        title="User_Missions"
        has-table
      >
        <TableUserMissions />

      </CardBox>









    </SectionMain>
  </LayoutAuthenticated>
</template>
