<script setup>

const props = defineProps({
	modelValue: Number
})

const emit = defineEmits(['update:modelValue'])

function toggle(ckw = true){
	if(ckw){
		if(props.modelValue + 1 > 3)
			return emit('update:modelValue', 0)
		return emit('update:modelValue', props.modelValue + 1)
	}
	
	if(props.modelValue - 1 < 0)
		return emit('update:modelValue', 3)
	return emit('update:modelValue', props.modelValue - 1)
}

</script>


<template>
	<div class="genious-switcher"
		 @click.prevent="toggle" 
		 @contextmenu.prevent="toggle(false)">
		<div class="genious-switcher__wrapper" :class="`active-${modelValue}`">
			<div class="genious-switcher__inner"></div>
		</div>

		<div class="genious-switcher__label">
			<slot/>
		</div>
	</div>
</template>

<style lang="scss">

$size: 44px;
$partSize: calc($size / 2);
$translate: calc($partSize - 2px);

.genious-switcher{

	display: flex;
	align-items: center;

	&__wrapper{
		position: relative;
		background-color: #efefef;
		border: 1px solid #ccc;
		border-radius: 15px;
		height: $size;
		width: $size;

		transition: background-color 300ms;

		&.active-1{
			background-color: #9999ff;

			> div{
				transform: translate($translate, 0);
			}
		}
		&.active-2{
			background-color: #99ff99;
			
			> div{
				transform: translate($translate, $translate);
			}
		}
		&.active-3{
			background-color: #ff9999;
			
			> div{
				transform: translate(0, $translate);
			}
		}
	}

	&__inner{
		position: absolute;
		height: $partSize;
		width: $partSize;
		border: 1px solid #ccc;
		background: #fff;
		border-radius: 100%;

		transition: transform 300ms;
	}

	&__label{
		margin-left: 15px;
	}
}
</style>