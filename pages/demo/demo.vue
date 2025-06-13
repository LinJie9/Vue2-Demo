<template>
	<view>
		
		<!-- <view class="demo-row">
			<view>111</view>
			<view>222</view>
			<view>333</view>
		</view> -->
		
		<view>
			<button @click="open()">打开</button>
		</view>
		
		<view class="box">
			<view>111</view>
			<view>222</view>
			<view>333</view>
		</view>
		
		
		<uni-popup ref="popup" type="bottom" background-color="#fff" border-radius="5rpx">
			<view style="height: 300rpx;">
				<view class="demo-row">
					<view>111</view>
					<view>222</view>
					<view>333</view>
				</view>
				<button @click="close()" style="width: 50%;">取消</button>
			</view>
		</uni-popup>
		
		<!-- 日期选择器 -->
		<u-datetime-picker :show="showDatePickerModal" :value="currentDateValue" mode="datetime" closeOnClickOverlay
			@confirm="handleDateConfirm" @cancel="closeDatePicker"></u-datetime-picker>
		
		<!-- 日期选择器弹窗 -->
		<u-modal :show="showDateModal" title="选择日期" closeOnClickOverlay @confirm="confirmDateRange"
			@cancel="cancelDateRange" :showCancelButton="true">
			<u--form labelPosition="left" :model="dateForm" ref="dateForm" labelWidth="150">
				<u-form-item label="开始日期" @click="showDatePicker(0)" borderBottom>
						<u--input disabled disabledColor="#ffffff" v-model="dateForm.startDate"
							placeholder="请选择开始日期"></u--input>
						<u-icon slot="right" name="calendar" size="23"></u-icon>
				</u-form-item>
				<u-form-item label="结束日期" @click="showDatePicker(1)" borderBottom>
					<u--input disabled disabledColor="#ffffff" v-model="dateForm.endDate"
						placeholder="请选择结束日期"></u--input>
					<u-icon slot="right" name="calendar" size="23"></u-icon>
				</u-form-item>
			</u--form>
		</u-modal>
		
		
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			const today = moment().format('YYYY-MM-DD');
			return {
				
				// 日期选择器
				dateForm: {
					startDate: today,
					endDate: today
				},
				showDateModal: false,
				showDatePickerModal: false,
				currentDateValue: today,
				currentDateType: 0, // 0:开始日期, 1:结束日期
				// 日期标题
				showDateRange: false,
				
			};
		},
		methods: {
			open(){
				this.$refs.popup.open()
			},
			close(){
				this.$refs.popup.close()
			}
		}
	}
</script>

<style lang="scss">
	page {
		// background-color: #f6f6fe;
		background-color: #f0f0f0;
	}
	
	.demo-item {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	
	.demo-row {
		display: flex;
		justify-content: space-around;
	}
	
	// 卡片盒
	.box {
		background-color: #fff;
		border-radius: 16rpx;
		padding: 24rpx;
		margin: 24rpx 24rpx;
		box-shadow: 0 8rpx 24rpx rgba(0, 0, 0, 0.1);
		transition: all 0.3s ease;
		border: 1rpx solid #f0f0f0;
	}
	
</style>
