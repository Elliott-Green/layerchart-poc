<script lang="ts">
	import {
		Area,
		AreaChart,
		Axis,
		ChartClipPath,
		Labels,
		LinearGradient,
		Spline,
		Svg
	} from 'layerchart';
	import { format, PeriodType } from '@layerstack/utils';
	import { cubicInOut } from 'svelte/easing';
	const mockDataPoints = [
		{
			date: new Date('2025-01-31T00:00:00.000Z'),
			value: 0
		},
		{
			date: new Date('2025-02-01T00:00:00.000Z'),
			value: 0
		},
		{
			date: new Date('2025-02-02T00:00:00.000Z'),
			value: 10
		},
		{
			date: new Date('2025-02-03T00:00:00.000Z'),
			value: 20
		},
		{
			date: new Date('2025-02-04T00:00:00.000Z'),
			value: 30
		},
		{
			date: new Date('2025-02-05T00:00:00.000Z'),
			value: 40
		},
		{
			date: new Date('2025-02-06T00:00:00.000Z'),
			value: 50
		},
		{
			date: new Date('2025-02-07T00:00:00.000Z'),
			value: 60
		},
		{
			date: new Date('2025-02-08T00:00:00.000Z'),
			value: 70
		},
		{
			date: new Date('2025-02-09T00:00:00.000Z'),
			value: 80
		},
		{
			date: new Date('2025-02-10T00:00:00.000Z'),
			value: 90
		},
		{
			date: new Date('2025-02-11T00:00:00.000Z'),
			value: 100
		},
		{
			date: new Date('2025-02-12T00:00:00.000Z'),
			value: 100
		}
	];
</script>

<div class=" h-[300px] mt-20">
	<AreaChart data={mockDataPoints} x="date" y="value" labels padding={{ left: 16, bottom: 24 }}>
		<Svg>
			<Axis placement="left" grid rule />
			<Axis
				placement="bottom"
				format={(d) => format(d, PeriodType.Day, { variant: 'short' })}
				rule
			/>
			<Spline draw={{ easing: cubicInOut, delay: 3000 }} class="stroke-2 stroke-secondary" />
			<ChartClipPath initialWidth={0} tweened={{ width: { duration: 3000, easing: cubicInOut } }}>
				<LinearGradient class="from-primary/50 to-primary/0" vertical let:gradient>
					<Area line={{ class: 'stroke-primary' }} fill={gradient} />
					<Labels format="integer" />
				</LinearGradient>
			</ChartClipPath>
		</Svg>
	</AreaChart>
</div>
<div class=" h-[300px]"><AreaChart data={mockDataPoints} x="date" y="value" /></div>
