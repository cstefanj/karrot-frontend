<template>
  <SidenavBox
    v-if="placeId"
    @toggle="$emit('toggleBox')"
    :expanded="$q.platform.is.mobile || expanded"
    :expandable="!$q.platform.is.mobile"
  >
    <template slot="icon">
      <QIcon name="fas fa-fw fa-shopping-cart" />
    </template>
    <template slot="name">
      {{ $t('GROUP.CURRENT_STORE') }}
    </template>
    <div
      slot="tools"
      class="tools"
    >
      <QBtn
        v-if="isEditor"
        flat
        dense
        round
      >
        <QIcon name="fas fa-fw fa-ellipsis-v" />
        <PlaceOptions/>
      </QBtn>
    </div>

    <QList
      highlight
      no-border
      class="no-padding"
    >
      <QItem :to="{name: 'placePickups', params: { placeId }}">
        <QItemSide class="text-center">
          <QIcon name="fas fa-shopping-basket" />
        </QItemSide>
        <QItemMain>
          {{ $t("GROUP.PICKUPS") }}
        </QItemMain>
      </QItem>
      <QItem :to="{name: 'placeFeedback', params: { placeId }}">
        <QItemSide class="text-center">
          <QIcon name="fas fa-balance-scale" />
        </QItemSide>
        <QItemMain>
          {{ $t("PICKUP_FEEDBACK.TITLE") }}
        </QItemMain>
      </QItem>
      <QItem :to="{name: 'placeHistory', params: { placeId }}">
        <QItemSide class="text-center">
          <i class="far fa-clock"/>
        </QItemSide>
        <QItemMain>
          {{ $t("GROUP.HISTORY") }}
        </QItemMain>
      </QItem>
    </QList>

  </SidenavBox>
</template>

<script>
import { QBtn, QList, QItem, QItemSide, QIcon, QItemMain } from 'quasar'
import SidenavBox from './SidenavBox'
import PlaceOptions from './PlaceOptions'

export default {
  props: {
    placeId: { default: null, type: Number },
    expanded: { default: true, type: Boolean },
    isEditor: { default: false, type: Boolean },
  },
  components: {
    SidenavBox, PlaceOptions, QBtn, QList, QItem, QItemSide, QIcon, QItemMain,
  },
}
</script>

<style scoped lang="stylus">
</style>