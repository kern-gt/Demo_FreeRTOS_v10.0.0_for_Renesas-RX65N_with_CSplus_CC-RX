# Demo_FreeRTOSv10.0.0_for_RenesasRX65N_with_CSplus_CC-RX

	このデモはFreeRTOSv10.0.0をRenesas RX65Nマイコン用に移植したものです。
	素人の自分が個人仕様目的で作成したものですのでこれに関する一切の責任を取りません。

	文字コードはUTF-8を使用いています。

動作環境：
	FreeRTOS:v10.0.0　(RX600 RXv2)
	開発環境：CS+forCC V6.01.00
	コンパイラ：CC-RX V2.08.00
	CPUボード：TARGET BOARD for RX65N(RTK5RX65N0C00000BR)
	CPU：R5F565NEDDFP

デモ内容：
	CPUボード上のLED0(PD6)を1Hz、LED1(PD7)を5Hzで点滅させる2つのタスクを動かします。

	クロック発生回路とポート初期化をスマートコンフィグレータで設定しています。
	FreeRTOSではカーネルタイマにCMT0,システムコールにソフトウェア割込み(SWINT)を使用している
	ので、その機能は使用しないでください。

ファイル構成：
	自力でプロジェクトを作るためのメモ。
	main.cとApplicationHook.cは自分が用意しています。

	１）FreeRTOSフォルダ以下をそのままプロジェクトフォルダにコピーしてプロジェクトに登録。
	２）ApplicationHook.cのフック関数類はユーザー側で定義しないとビルド通らないので、取りあえずこれもコピーしてプロジェクトに登録。
	３）main.cにあるvApplicationSetupTimerInterrupt()も必ず必要なので適当にどこかに定義する。
	４）/FreeRTOS/FreeRTOSConfig.hを目的に合わせて設定する。

注意点：
	・ソースコードの文字エンコードにUTF-8を使用するため、ビルド設定をShift-JISからUTF-8に変更してあります。
	・FreeRTOSのメモリ管理ファイルは「heap_1.c」を使用しています。目的に応じて変更してください。
	・