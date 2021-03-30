<template>
  <div>
    <section class="heading">
      <div>
        <h1 class="title">ウマ娘のヒミツジェネレーター（仮）</h1>
      </div>
      <div>
        <p class="exp">
          非公式のお遊びツールです。
          まだいないキャラはそのうち増えるかもしれないです。
        </p>
      </div>
    </section>
    <section class="view">
      <div class="columns">
        <kanvas
          :name-text="inputData.name"
          :title-text="inputData.title"
          :body-text="inputData.body"
          :icon="inputData.icon.icon"
        />
      </div>
    </section>
    <section class="controler">
      <b-field label="ウマ娘の名前" label-position="on-border">
        <b-input
          v-model="inputData.name"
          placeholder="トウカイテイオー"
          rounded
        ></b-input>
      </b-field>
      <b-field label="アイコン" label-position="on-border">
        <b-select v-model="inputData.icon" placeholder="設定するアイコン">
          <option v-for="uma in umaList" :key="uma.id" :value="uma">
            {{ uma.name }}
          </option>
        </b-select>
      </b-field>
      <b-field label="ヒミツの内容" label-position="on-border">
        <b-input
          v-model="inputData.body"
          type="textarea"
          rows="2"
          maxlength="48"
          placeholder="実は、..."
          rounded
        >
        </b-input>
      </b-field>
    </section>
  </div>
</template>

<script>
import kanvas from '@/components/Kanvas'
import UMA from '~/constants/uma'
export default {
  name: 'Umagen',
  components: { kanvas },
  data() {
    return {
      umaList: UMA,
      inputData: {
        name: '',
        body: '',
        title: '',
        icon: { id: 0, name: '画像なし', icon: './icon/none.png' },
      },
    }
  },
}
</script>
<style lang="scss" scoped>
.heading,
.controler,
.view {
  margin: 24px 18px;
}
.heading {
  width: 800px;
}
.controler {
  width: 600px;
}

.title {
  font-size: 42px;
  font-family: 'Wanpaku';
}
.exp {
  margin-top: 4px;
  font-size: 11px;
}
</style>
