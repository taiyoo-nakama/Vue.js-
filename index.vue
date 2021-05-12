
 <template>
  <div class="example">
    <div class="tabs">
      <TabItem v-for="item in list" v-bind="item" :key="item.id" v-model="currentId" />
    </div>
    <div class="contents">
      <transition>
        <section class="item" :key="currentId">
          {{ current.content }}
        </section>
      </transition>
    </div>
  </div>
</template>

<script>
  import TabItem from './TabItem.vue'
  export default {
    components: { TabItem },
    data() {
      return {
        currentId: 1,
        list: [
          { id: 1, label: 'Tab1', content: 'コンテンツ1' },
          { id: 2, label: 'Tab2', content: 'コンテンツ2' },
          { id: 3, label: 'Tab3', content: 'コンテンツ3' }
        ]
      }
    },
    computed: {
      current() {
        return this.list.find(el => el.id === this.currentId) || {}
      }
    }
  }
</script>

  <style>
    .tab-style{
      display: flex;
      color: white;
      background-color: black;
      list-style: none;
    }
  </style>