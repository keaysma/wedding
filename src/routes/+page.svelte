<script lang="ts">
	import { onMount } from "svelte";

    // Reactive variables to store mouse coordinates
    let pageX = $state(0);
    let pageY = $state(0);

    // Function to update the coordinates on mouse movement
    function handleMousemove(event: MouseEvent) {
        pageX = (event.pageX / window.innerWidth);
        pageY = (event.pageY / window.innerHeight);
    }

    const tMillisSeconds = 1000;
    const tSecondsMinutes = 60;
    const tMinutesHours = 60;
    const tHoursDays = 24;
    const tDaysWeeks = 7;

    let eventTime = new Date("October 24 2026, 11:00 EDT");

    function getRemainingTime (): {
        weeks: string,
        days: string,
        hours: string,
        minutes: string,
        seconds: string,
    } {
        const remainingMillis = Number(eventTime) - Number(new Date());

        const totalWeeks = remainingMillis / (tMillisSeconds * tSecondsMinutes * tMinutesHours * tHoursDays * tDaysWeeks);
        const weeks = Math.trunc(totalWeeks).toString().padStart(2, "0");
        
        const remainingDays = remainingMillis % (tMillisSeconds * tSecondsMinutes * tMinutesHours * tHoursDays * tDaysWeeks);
        const totalDays = remainingDays / (tMillisSeconds * tSecondsMinutes * tMinutesHours * tHoursDays);
        const days = Math.trunc(totalDays).toString().padStart(2, "0");

        const remainingHours = remainingMillis % (tMillisSeconds * tSecondsMinutes * tMinutesHours * tHoursDays);
        const totalHours = remainingHours / (tMillisSeconds * tSecondsMinutes * tMinutesHours);
        const hours = Math.trunc(totalHours).toString().padStart(2, "0");

        const remainingMinutes = remainingMillis % (tMillisSeconds * tSecondsMinutes * tMinutesHours);
        const totalMinutes = remainingMinutes / (tMillisSeconds * tSecondsMinutes);
        const minutes = Math.trunc(totalMinutes).toString().padStart(2, "0");

        const remainingSeconds = remainingMillis % (tMillisSeconds * tSecondsMinutes);
        const totalSeconds = remainingSeconds / (tMillisSeconds);
        const seconds = Math.trunc(totalSeconds).toString().padStart(2, "0");

        return {
            weeks,
            days,
            hours,
            minutes,
            seconds,
        }
    }

    let remaining = $state(getRemainingTime());

    onMount(() => {
        setInterval(() => {
            remaining = getRemainingTime();
        }, 1_000);
    });
</script>

<svelte:window on:mousemove={handleMousemove} />

<section class="header">
    <h1>Raquel & Michael</h1>
    <h2>October 24, 2026, 11AM • Lucketts, VA</h2>

    <!-- <div class="polaroid" style="transform: rotate3d({(1 - (pageY * 2))}, {-1 + (pageX * 2)}, 0.1, 10deg) scale3d(0.95, 0.95, 0.95) translate3d(-5px, 5px, 0px);"> -->
    <div class="polaroid" style="transform: rotate3d({0.75 + (pageX - 0.5)}, {0.5 + (pageY - 0.5)}, 0.1, 9deg) scale3d(0.95, 0.95, 0.95) translate3d(-5px, 5px, 0px);">
            <img  src="RM-Sunset-1.jpg" alt="That's us <3" />
            <span class="mark"><span class="digit">{remaining.weeks}</span> WEEKS, <span class="digit">{remaining.days}</span> DAYS, <span class="digit">{remaining.hours}</span> HOURS, <span class="digit">{remaining.minutes}</span> MINUTES, <span class="digit">{remaining.seconds}</span> SECONDS</span>
    </div>

    <div class="button-group">
        <a class="button-like rsvp" target="_blank" href="https://sheetasfamily.planningpod.com/index.cfm?#rsvp-panel">RSVP</a>
        <!-- svelte-ignore a11y_missing_attribute -->
        <a class="button-like registry">Registry</a>
        <a class="button-like directions" target="_blank" href="https://maps.app.goo.gl/TdLEcWCqyf4RmQeW8">Directions</a>
    </div>
</section>

<style lang="scss">
    a.button-like {
        display: block;

        padding: 0.5em;

        background-color: var(--foreground-color);
        color: var(--background-color);

        border: 2px solid var(--foreground-color);

        font-size: 1.5em;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 200;

        white-space: pre;
        text-decoration: none;

        transition: all 0.5s;

        &:hover {
            color: white;
            border-color: black;
            background-color: black;
        }

        &.registry {
            cursor: not-allowed;
            background-color: var(--background-disabled);
            border-color: var(--background-disabled);

            &:hover {
                color: var(--background-color);
            }
        }
    }

    .button-group {
        display: flex;
        gap: 0.25em;

        width: 100%;

        margin: auto auto 2em;

        > * {
            flex: 1;
        }

        @media screen and (max-width: 768px) {
            flex-direction: column;
        }
    }

    .polaroid {
        position: relative;
        
        width: min(850px, 100%);

        margin: auto;

        > img {
            width: 100%;
            display: block;
            box-shadow: 
                 4px  4px 8px var(--dropshadow-color), 
                 4px -4px 8px var(--dropshadow-color),
                -4px -4px 8px var(--dropshadow-color), 
                -4px  4px 8px var(--dropshadow-color); 
            border: 5px solid white;
            border-bottom-width: 30px;
        }
        
        > span.mark {
            position: absolute;
            right: 0;
            bottom: 2em;
            margin: 0 0.25em 0.25em 0;

            font-family: "Digital-7";

            color: var(--mark-timer-color);
            mix-blend-mode: hard-light;

            .digit {
                font-family: "7Segment";
            }
        }
    }

    section.header {
        position: relative;
        display: flex;
        flex-direction: column;
        text-align: center;
        
        padding: 2em 0 0;
        margin: auto;
        max-width: 768px;
        height: min(1010px, calc(100% - 4vh));


        h1 {
            font-family: "Fleur De Leah";
            font-size: min(12vw, 7em);
            margin: 0;
            color: var(--foreground-color);
        }

        h2 {
            font-size: min(4.5vw, 2.5em);
            color: var(--foreground-color);
            margin: 0;
        }
    }
</style>
