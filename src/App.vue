<template>
  <div id="app">
    <!-- htmlタグを含むデータの送る側 -->
    <!-- htmlタグを含んで送るにはコンポーネントの中に書くと送れる。 -->
    <!-- propsとの違いは、htmlテンプレートごと送信できる点にある -->
    <LikeHeader headerText="Hello">
      <h1>HTMLテンプレートを親コンポーネントから送信</h1>
      <h2>{{ number }}</h2>

      <!-- 名前付きスロット作成方法(送る側) -->
      <!-- ①送りたい要素をtemplateタグで囲う -->
      <!-- ②v-slot:名前という属性を与えてその中で送りたい特定のHTMLテンプレートを指定 -->
      <template v-slot:title>
        <h1>v-slotのタイトル</h1>
      </template>
      <h3>デフォルトスロット</h3>
      <template v-slot:number>
        <h2>{{ number }}</h2>
      </template>

      <!-- slotプロパティを使用して値を表示する -->
      <!-- データの表示方法はv-slot:title='好きな名前'と定義することで'好きな名前'が子コンポーネントで送信した値に変わる。(今回はuserというオブジェクトになる) -->
      <template v-slot:title2="slotProps">
        <h1>子コンポーネントからのデータ</h1>
        <h2>{{ slotProps.user.firstName }}</h2>
        <h2>{{ slotProps.user.lastName  }}</h2>
      </template>

    <!-- 動的にタイトルを指定することができる -->
    <template v-slot:[sample]>
      <h1>動的にスロット名を指定</h1>
    </template>

    <!-- 省略記法 v-slot:は#に置き換えできる -->
    <template #[sample2]>
      <h1>v-slotの省略記法サンプル</h1>
    </template>

    </LikeHeader>
    <!-- slotプロパティを使用して値を表示。かつコンポーネント内にtemplateタグがない場合(デフォルトtemplateのみしかない場合)はtemplateタグを用意しなくてもslotプロパティを使用できる。-->
    <!-- またdefaultの表示も省略できる -->
    <!-- LikeHeaderが今回は二つ存在しているので使えない為コメントアウトしている -->
    <!-- <LikeHeader v-slot:default="slotProps">
      <LikeHeader v-slot="slotProps">
      <h1>2つ目のLikeHeader</h1>
      {{ slotProps }}
    </LikeHeader> -->
  </div>
</template>

<script>
import LikeHeader from './components/LikeHeader.vue'

export default {
  data() {
    return {
      number: 14,
      sample: 'title3',
      sample2: 'title4'
    }
  },
  components: {
    LikeHeader
  },
}
</script>

<style scoped>
  /* h1 {
    color: blue;
  } */
</style>
