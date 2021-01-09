<template>
  <div id="container" class="jsfiddle-container">
  <form autocomplete="nope">

    <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
      <input class="mdl-textfield__input" type="text" id="zip"  autocomplete="nope">
      <label class="mdl-textfield__label" for="zip" >郵便番号を入力</label>
    </div>

    <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
      <input class="mdl-textfield__input" type="text" id="state" autocomplete="nope">
      <label class="mdl-textfield__label" for="state">都道府県</label>
    </div>

    <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
      <input class="mdl-textfield__input" type="text" id="city" autocomplete="nope">
      <label class="mdl-textfield__label" for="city">市区町村</label>
    </div>

    <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
      <input class="mdl-textfield__input" type="text" id="street" autocomplete="nope">
      <label class="mdl-textfield__label" for="street">町域</label>
    </div>


  </form>
</div>
</template>

<script>
  // APIキーを指定して住所補完サービスを作成
  var api = new postcodejp.address.AutoComplementService('JSROs8akSxHGYQ4KL4Tc9CXY2pXTc0dXrAay9kG');

// 郵便番号テキストボックスを指定
api.setZipTextbox('zip')

// 住所補完フィールドを追加
api.add(new postcodejp.address.StateTextbox('state'));
api.add(new postcodejp.address.TownTextbox('city'));
api.add(new postcodejp.address.StreetTextbox('street'));


api.setAdditionalCallback(function(data) {
  mdlCleanUp();
});
// 郵便番号テキストボックスの監視を開始
api.observe();

</script>