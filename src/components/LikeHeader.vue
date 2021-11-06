<template>
  <div>
    <!-- htmlタグを含むデータの受け側 -->
    <!-- slotタグを書くと親コンポーネントで定義したHTML要素を含むデータを受け取ることができる -->
    <slot>
      <!-- フォールバックコンテンツ -->
      <!-- slotの中身が何もない場合のみ表示されるもの。今回は「デフォルトのタイトル」と表示される。 -->
      <h1>デフォルトのタイトル</h1>
    </slot>
    <!-- slotは複数指定することもできる -->
    <!-- 名前付きスロット作成方法(受け側) -->
    <!-- 使用したいv-slotの親コンポーネントで指定した名前をname属性として指定することで完了 -->
    <slot name="title"></slot>
    <hr>
    <slot name="number"></slot>
    <hr>

    <!-- 名前の付いていないslotはデフォルトスロットと呼ぶ -->
    <!-- これはtemplateタグで囲われていない要素全てを上から順に表示してくれる -->
    <!-- 実際はVue側が自動的にtemplateタグで、囲われていないものをv-slot="default"という名前で囲って子コンポーネントに持ってきてくれる。つまりv-slot:defaultが省略された形で書いても表示される仕様となっている -->
    <slot></slot>

    <!-- あまり使わないけど子コンポーネントから親コンポーネントにデータを渡すことができる -->
    <!-- やり方：v-bind:送りたいデータ='好きな名前'で送信できる -->
    <slot name="title2" v-bind:user='user'></slot>

    <slot name="title3"></slot>
    <slot name="title4"></slot>
  </div>
</template>

<script>

export default {

  data() {
    return {
      user: {
        firstName:'ドナルド',
        lastName: 'トランプ',
      }
    }
  }
}
</script>

<!-- slotの中身データの変更はprops同様変更できない。ただしstyleに関しては子コンポーネント内でも変更させることができる。 -->
<style scoped>
  h1 {
    color: red;
  }
</style>
