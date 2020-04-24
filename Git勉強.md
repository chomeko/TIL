# もくもく会で勉強したgit

バージョン管理　git

.git
ローカル/リモート　リポジトリ
ローカル=pc
リモート=github

git initをすると今いるフォルダにgitのリポジトリを作る
git add ステージングする
git commit コミットする（gitに保存する）
git push (ローカルからリモートに送る)

git add .　(全てのファイル)
git add index.htmlでステージングを指定できる
git commit -m "コメントをつけてステージングをコミットをする"

ローカルからリモートに同期する
git push origin master　省略可　git push

各コミットに戻ることもできる
最初のコミット　4/23 10:00
コメントをつけてステージングをコミットをする 4/24 11:00

bransh　（枝）
ブランチを新しく作る時
git checkout -b "dev/login"
マージする
git checkout masterに戻る
git marge dev/login
