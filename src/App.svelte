<script>
	import {
		Button,
		InputGroup,
		InputGroupAddon,
		Input,
	} from 'sveltestrap';
	import {
		onMount
	} from "svelte";

	const palettes = [{
			name: 'frozen-rose',
			colors: ['#29368f', '#e9697b', '#1b164d', '#f7d996'],
			background: '#f2e8e4',
		},
		{
			name: 'winter-night',
			colors: ['#122438', '#dd672e', '#87c7ca', '#ebebeb'],
			background: '#ebebeb',
		},
		{
			name: 'saami',
			colors: ['#eab700', '#e64818', '#2c6393', '#eecfca'],
			background: '#e7e6e4',
		},
		{
			name: 'knotberry1',
			colors: ['#20342a', '#f74713', '#686d2c', '#e9b4a6'],
			background: '#e5ded8',
		},
		{
			name: 'knotberry2',
			colors: ['#1d3b1a', '#eb4b11', '#e5bc00', '#f29881'],
			background: '#eae2d0',
		},
		{
			name: 'tricolor',
			colors: ['#ec643b', '#56b7ab', '#f8cb57', '#1f1e43'],
			background: '#f7f2df',
		},
		{
			name: 'foxshelter',
			colors: ['#ff3931', '#007861', '#311f27', '#bab9a4'],
			background: '#dddddd',
		},
		{
			name: 'hermes',
			colors: ['#253852', '#51222f', '#b53435', '#ecbb51'],
			background: '#eeccc2',
		},
		{
			name: 'olympia',
			colors: ['#ff3250', '#ffb33a', '#008c36', '#0085c6', '#4c4c4c'],
			stroke: '#0b0b0b',
			background: '#faf2e5',
		},
		{
			name: 'byrnes',
			colors: ['#c54514', '#dca215', '#23507f'],
			stroke: '#0b0b0b',
			background: '#e8e7d4',
		},
		{
			name: 'butterfly',
			colors: ['#f40104', '#f6c0b3', '#99673a', '#f0f1f4'],
			stroke: '#191e36',
			background: '#191e36',
		},
		{
			name: 'floratopia',
			colors: ['#bf4a2b', '#cd902a', '#4e4973', '#f5d4bc'],
			stroke: '#1e1a43',
			background: '#1e1a43',
		},
		{
			name: 'verena',
			colors: ['#f1594a', '#f5b50e', '#14a160', '#2969de', '#885fa4'],
			stroke: '#1a1a1a',
			background: '#e2e6e8',
		},
		{
			name: 'florida_citrus',
			colors: ['#ea7251', '#ebf7f0', '#02aca5'],
			stroke: '#050100',
			background: '#9ae2d3',
		},
		{
			name: 'lemon_citrus',
			colors: ['#e2d574', '#f1f4f7', '#69c5ab'],
			stroke: '#463231',
			background: '#f79eac',
		},
		{
			name: 'yuma_punk',
			colors: ['#f05e3b', '#ebdec4', '#ffdb00'],
			stroke: '#ebdec4',
			background: '#161616',
		},
		{
			name: 'moir',
			colors: ['#a49f4f', '#d4501e', '#f7c558', '#ebbaa6'],
			stroke: '#161716',
			background: '#f7f4ef',
		},
		{
			name: 'sprague',
			colors: ['#ec2f28', '#f8cd28', '#1e95bb', '#fbaab3', '#fcefdf'],
			stroke: '#221e1f',
			background: '#fcefdf',
		},
		{
			name: 'bloomberg',
			colors: ['#ff5500', '#f4c145', '#144714', '#2f04fc', '#e276af'],
			stroke: '#000',
			background: '#fff3dd',
		},
		{
			name: 'revolucion',
			colors: ['#ed555d', '#fffcc9', '#41b797', '#eda126', '#7b5770'],
			stroke: '#fffcc9',
			background: '#2d1922',
		},
		{
			name: 'sneaker',
			colors: ['#e8165b', '#401e38', '#66c3b4', '#ee7724', '#584098'],
			stroke: '#401e38',
			background: '#ffffff',
		},
		{
			name: 'miradors',
			colors: ['#ff6936', '#fddc3f', '#0075ca', '#00bb70'],
			stroke: '#ffffff',
			background: '#020202',
		},
		{
			name: 'kaffeprat',
			colors: ['#BCAA8C', '#D8CDBE', '#484A42', '#746B58', '#9A8C73'],
			stroke: '#000',
			background: '#fff',
		},
		{
			name: 'rag-mysore',
			colors: ['#ec6c26', '#613a53', '#e8ac52', '#639aa0'],
			background: '#d5cda1'
		},
		{
			name: 'rag-gol',
			colors: ['#d3693e', '#803528', '#f1b156', '#90a798'],
			background: '#f0e0a4'
		},
		{
			name: 'rag-belur',
			colors: ['#f46e26', '#68485f', '#3d273a', '#535d55'],
			background: '#dcd4a6'
		},
		{
			name: 'rag-bangalore',
			colors: ['#ea720e', '#ca5130', '#e9c25a', '#52534f'],
			background: '#f9ecd3'
		},
		{
			name: 'rag-taj',
			colors: ['#ce565e', '#8e1752', '#f8a100', '#3ac1a6'],
			background: '#efdea2'
		},
		{
			name: 'rag-virupaksha',
			colors: ['#f5736a', '#925951', '#feba4c', '#9d9b9d'],
			background: '#eedfa2'
		},
		{
			name: 'tsu_arcade',
			colors: ['#4aad8b', '#e15147', '#f3b551', '#cec8b8', '#d1af84', '#544e47'],
			background: '#cfc7b9'
		},
		{
			name: 'tsu_harutan',
			colors: ['#75974a', '#c83e3c', '#f39140', '#e4ded2', '#f8c5a4', '#434f55'],
			background: '#cfc7b9'
		},
		{
			name: 'tsu_akasaka',
			colors: ['#687f72', '#cc7d6c', '#dec36f', '#dec7af', '#ad8470', '#424637'],
			background: '#cfc7b9'
		},
		{
			name: 'hilda01',
			colors: ['#ec5526', '#f4ac12', '#9ebbc1', '#f7f4e2'],
			background: '#e7e8d4'
		},
		{
			name: 'hilda02',
			colors: ['#eb5627', '#eebb20', '#4e9eb8', '#f7f5d0'],
			background: '#77c1c0'
		},
		{
			name: 'hilda03',
			colors: ['#e95145', '#f8b917', '#b8bdc1', '#ffb2a2'],
			background: '#6b7752'
		},
		{
			name: 'hilda04',
			colors: ['#e95145', '#f6bf7a', '#589da1', '#f5d9bc'],
			background: '#f5ede1'
		},
		{
			name: 'empusa',
			colors: ['#c92a28', '#e69301', '#1f8793', '#13652b', '#e7d8b0', '#48233b', '#e3b3ac'],
			stroke: '#1a1a1a',
			background: '#f0f0f2',
		},
		{
			name: 'delphi',
			colors: ['#475b62', '#7a999c', '#2a1f1d', '#fbaf3c', '#df4a33', '#f0e0c6', '#af592c'],
			stroke: '#2a1f1d',
			background: '#f0e0c6',
		},
		{
			name: 'mably',
			colors: [
				'#13477b',
				'#2f1b10',
				'#d18529',
				'#d72a25',
				'#e42184',
				'#138898',
				'#9d2787',
				'#7f311b',
			],
			stroke: '#2a1f1d',
			background: '#dfc792',
		},
		{
			name: 'nowak',
			colors: ['#e85b30', '#ef9e28', '#c6ac71', '#e0c191', '#3f6279', '#ee854e', '#180305'],
			stroke: '#180305',
			background: '#ede4cb',
		},
		{
			name: 'jupiter',
			colors: ['#c03a53', '#edd09e', '#aab5af', '#023629', '#eba735', '#8e9380', '#6c4127'],
			stroke: '#12110f',
			background: '#e6e2d6',
		},
		{
			name: 'hersche',
			colors: [
				'#df9f00',
				'#1f6f50',
				'#8e6d7f',
				'#da0607',
				'#a4a5a7',
				'#d3d1c3',
				'#42064f',
				'#25393a',
			],
			stroke: '#0a0a0a',
			background: '#f0f5f6',
		},
		{
			name: 'cherfi',
			colors: ['#99cb9f', '#cfb610', '#d00701', '#dba78d', '#2e2c1d', '#bfbea2', '#d2cfaf'],
			stroke: '#332e22',
			background: '#e3e2c5',
		},
		{
			name: 'harvest',
			colors: [
				'#313a42',
				'#9aad2e',
				'#f0ae3c',
				'#df4822',
				'#8eac9b',
				'#cc3d3f',
				'#ec8b1c',
				'#1b9268',
			],
			stroke: '#463930',
			background: '#e5e2cf',
		}
	];

	let palette = {
		name: 'frozen-rose',
		colors: ['#29368f', '#e9697b', '#1b164d', '#f7d996'],
		background: '#f2e8e4',
	};

	const directions = [-1, 0, 1];
	const finalSize = 10;
	const offset = 2;
	let startSteps = 3;
	let drawing = true;
	let canvas, context, cssPadding, canvasPadding, size, dpr, tileStep, startSize;

	onMount(() => {
		canvas = document.querySelector('canvas');
		context = canvas.getContext('2d');
		canvasPadding = 200;
		if (window.innerWidth < 600 || window.innerHeight < 600) {
			canvasPadding = 80;
		}
		size = window.innerWidth < window.innerHeight ? window.innerWidth - canvasPadding : window.innerHeight - canvasPadding;
//		dpr = window.devicePixelRatio;
		canvas.width = size;
		canvas.height = size ;
//		context.scale(dpr, dpr);
		context.lineWidth = 2;

		tileStep = (size - offset * 2) / 8;
		startSize = tileStep;

		tile();
	});

	function sleep(milliseconds) {
		return new Promise(resolve => setTimeout(resolve, milliseconds))
	}

	function draw(x, y, width, height, xMovement, yMovement, steps) {
		if (!drawing) {
			return;
		}
		context.beginPath();
		context.rect(x, y, width, height);
		context.strokeStyle = palette.background;
		context.fillStyle = selectColor();
		context.fill();
		context.stroke();
		let sum = 900;
		if (steps < 0) {
			steps = 1 + Math.floor(Math.random() * 3);
			sum = 2000;
		}
		const newSize = startSize * (steps / startSteps) + finalSize;
		const newX = x + (width - newSize) / 2;
		const newY = y + (height - newSize) / 2;
		const skewX = newX - ((x - newX) / (steps + 2)) * xMovement;
		const skewY = newY - ((y - newY) / (steps + 2)) * yMovement;
		sleep(Math.random() * sum + sum).then(() => {
			draw(skewX, skewY, newSize, newSize, xMovement, yMovement, steps - 1);
		})
	}

	function tile() {
		stop();
		drawing = true;
		context.strokeStyle = palette.background;
		context.fillStyle = palette.background;
		context.fillRect(0, 0, canvas.width, canvas.height);
		for (let x = offset; x < size - offset; x += tileStep) {
			for (let y = offset; y < size - offset; y += tileStep) {
				const xDirection = directions[Math.floor(Math.random() * directions.length)];
				const yDirection = directions[Math.floor(Math.random() * directions.length)];

				startSteps = 2 + Math.floor(Math.random() * 2);
				draw(x, y, startSize, startSize, xDirection, yDirection, startSteps - 1);
			}
		}
	}

	function selectColor() {
		return palette.colors[Math.floor(Math.random() * (palette.colors.length - 0.05))];
	}

	function stop() {
		drawing = false;
	}
</script>

<style>
	canvas {
		display: block;
		outline: 1px solid #999;
		box-shadow: 1px 10px 15px #888888;
		margin: 20px auto;
	}
	:global(body) {
		margin: 0;
		background-color: #ffffff;
		background-image: url("data:image/svg+xml,%3Csvg width='70' height='70' viewBox='0 0 70 70' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23000000' fill-opacity='0.06' fill-rule='evenodd'%3E%3Cpath d='M0 0h35v35H0V0zm5 5h25v25H5V5zm5 5h15v15H10V10zm5 5h5v5h-5v-5zM40 5h25v25H40V5zm5 5h15v15H45V10zm5 5h5v5h-5v-5zM70 35H35v35h35V35zm-5 5H40v25h25V40zm-5 5H45v15h15V45zm-5 5h-5v5h5v-5zM30 40H5v25h25V40zm-5 5H10v15h15V45zm-5 5h-5v5h5v-5z'/%3E%3C/g%3E%3C/svg%3E");
	}
</style>

<div>
	<InputGroup class="colorselect" style="max-width: {size+10}px;margin: auto;">
		<InputGroupAddon addonType="prepend">
			<Button color="danger" on:click={stop}>Stop</Button>
			<Button color="primary" on:click={tile}>Start</Button>
			{#each palette.colors as color}
		    <div class="colordiv" style="background: {color};width: 20px;"></div>
	   	{/each}
	  </InputGroupAddon>
	  <Input type="select" bind:value={palette}>
	  {#each palettes as paletteOption}
    	<option value={paletteOption}>{paletteOption.name}</option>
  	{/each}
	  </Input>
  </InputGroup>
  <canvas style="border: 4px solid {palette.background};"></canvas>
</div>
