<template>
	<div :style="block">
		<svg viewBox="0 0 36 36" class="c-prog">
			<path class="c-prog__circle"
				:stroke-dasharray="progress"
				:style="circle"
				d="M18 2.0845
				a 15.9155 15.9155 0 0 1 0 31.831
				a 15.9155 15.9155 0 0 1 0 -31.831"
			/>
		</svg>
	</div>
</template>

<style>
	.c-prog {
		display: block;
	}

	.c-prog__circle {
		fill: none;
		stroke-linecap: round;
		animation: progress 1s ease-out forwards;
	}

	@keyframes progress {
		0% {
			stroke-dasharray: 0 100;
		}
	}
</style>

<script>
	export default {
		props: [
			'diameter',
			'color',
			'total',
			'completed',
			'width'
		],
		computed: {
			block () {
				return {
					height: `${this.diameter ? this.diameter : 100}px`,
					width: `${this.diameter ? this.diameter : 100}px`
				}
			},
			progress () {
				return `${this.completed / this.total * 100}, 100`
			},
			circle () {
				return {
					stroke: `${this.color ? this.color : 'green'}`,
					strokeWidth: `${this.width ? this.width : '2'}`
				}
			}
		}
	}
</script>