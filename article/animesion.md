# Androidアプリのアニメーション

****

## なんでAndroindのアニメーションやるねん？

****
４月８日

もう正直何をしても結局失敗すると思いたくなくても
おもってしまい、何もできずにいた。

しかし何かしないと激しい虚無感に永遠に襲われる。

とりあえず何かしようと思ったら
浜ちゃんからアニメーション調べてくれ（本人は忘れてるだろうが）
と言われていたのでとりあえずやることにした。

別に学校のためでも就活もないからオラちょっとワクワクしてきたぞ！



### アニメーション使うメリット

***

やっぱりアプリ内で何が起こってるかがすぐにわかること

そしてやっぱりなんかすごいアプリに見える事！！

とりあえずこんな感じか

### とりあえずこんなの作りたい

***

昔モンスターハンターをPSPポータブルでやってた身
としてはあのPSP起動した時のアニメーションみたいに
アプリ開いた時のアニメーション作ってみよかな

### アニメーションをAndroidで実装する方法
****

物理学ベースのモーションがあるらしいのでもうちょい
深く調べてみっか

### 物理学ベースのアニメーション

****

よく分からんので一旦スルー

### 公式動画でのアニメーション

***

公式が教えてくれたアニメーションは
四角が大きくなったり小さくなったりする際に
アニメーションを加え動いてる様に見える様にする（日本語へたですまん）
```kotlin
private enum class BoxState{
    Small,
    Large
}

@SuppressLint("UnusedTransitionTargetStateParameter")
@Composable
fun UpdateTransitionDemo(){
    var boxstate by remember{ mutableStateOf(BoxState.Small)}
    val transition = updateTransition(targetState = boxstate)
    val color by transition.animateColor() { state ->
        when(state){
            BoxState.Small -> Blue
            BoxState.Large -> Red
        }
    }

    val size by transition.animateDp() {state ->
        when(boxstate){
            BoxState.Small -> 64.dp
            BoxState.Large -> 128.dp
        }
    }

    Column() {
        Button(
            onClick = {
                boxstate = when(boxstate){
                    BoxState.Small -> BoxState.Large
                    BoxState.Large -> BoxState.Small
                }
            }
        ){
            Text("CHANGE COLOR")
        }
        Spacer(modifier = Modifier.height(size))

        Box(
            modifier = Modifier
                .size(size)
                .background(color)
        )
    }
}
```

コード載せとく








