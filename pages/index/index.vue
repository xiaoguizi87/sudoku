<template>
	<view class='flex flex-direction align-center padding justify-center'>
		<view class='head'>
			<!--button class='btn' hover-class='btn-hover'>占位符</button-->
			<view>
<!-- 				<text>耗时：{{timeElapse}}</text>
 -->			</view>
			<!-- <button class='btn' hover-class='btn-hover' catchtap='goToMenu'>使用说明</button> -->
		</view>

		<view class='flex'>
			<view v-for='(r, i) in board' :key='i' class='row'>
				<view class='cell' v-for='(c, j) in r' :key='j' :class="{empty: board[i][j] === ' ', selected: i === selectedX && j === selectedY}" @click='inputNum(i, j)'>
					{{c}}
				</view>
			</view>
		</view>

		<view class='input-row'>
			<view class='input-num' v-for='(i, k) in numbers' :key='k'>{{i}}</view>
		</view>

		<view class='bottom'>
<!-- 			<button class='btn' hover-class='btn-hover' catchtap='clean'>清零</button>
			<button class='btn' hover-class='btn-hover' catchtap='doSolve'>求解</button> -->
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				board: [
					[' ', ' ', ' ', ' '],
					['3', ' ', ' ', ' '],
					[' ', ' ', '4', ' '],
					[' ', '2', '3', ' ']
				],
				notEmptyPos: [],
				numbers: [1, 2, 3, 4, "X"],
				selectedX: -1,
				selectedY: -1,
			};
		},
		methods: {
			inputNum(i, j) {
					console.log(i, j)
					this.selectedX = i
					this.selectedY = j
			} 
		},
		onLoad() {
			console.log('hello')
			for (let i = 0; i < this.board.length; i++) {
				for (let j = 0; j < this.board[i].length; j++) {
					if ((this.board[i][j]) !== ' ') {
						this.notEmptyPos.push([i, j])
					}
				}
			}
		}
	}
</script>

<style lang="scss">
	page {
		padding-top: 40px;
	}

	.cell {
		// background: #e5e5e5;
		// /* 长宽超过此值，在ide中的ipad机型上以及真机的荣耀8手机上，会出现整体高度不足的问题，某些cell就会被压缩导致框线丢失和方框变扁 */
		width: 108rpx;
		height: 108rpx;
		line-height: 104rpx;
		font-size: 20px;
		font-color: blue;
		text-align: center;
		border: 2rpx solid lightgray;
	}
	
	.empty {
		background: white;
	}
	
	.selected {
		background: pink;
	}
	.row:first-child {
		border-left: solid;
	}

	.row:nth-child(2n) {
		border-right: solid;
	}

	.cell:first-child {
		border-top: solid;
	}

	.cell:nth-child(2n) {
		border-bottom: solid;
	}

	/*============================================*/
	.btn {
		background: white;
		border-radius: 10rpx;
		border-width: 0;
		padding: 0;
		margin: 0;
		width: 150rpx;
		height: 80rpx;
		/*text-align: center;*/
		display: inline-block;
	}

	.btn-hover {
		background: #bbbbbb;
		color: white;
	}

	.head {
		display: flex;
		justify-content: space-between;
		padding-top: 25rpx;
		padding-bottom: 25rpx;
	}

	.input-row {
		display: flex;
		justify-content: space-around;
		margin-top: 25rpx;
		width: 80vw;
	}

	.input-num {
		display: inline-block;
		width: 100rpx;
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
		border: 2rpx solid skyblue;
	}

	.input-num.red {
		color: red;
	}

	.bottom {
		display: flex;
		justify-content: space-around;
		padding-top: 25rpx;
		margin-bottom: 25rpx;
	}
</style>
