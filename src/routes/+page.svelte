<script lang="ts">
	import { onMount } from "svelte";

    // Reactive variables to store mouse coordinates
    let pageX = $state(0);
    let pageY = $state(0);

    // Function to update the coordinates on mouse movement
    function handleMousemove(event: MouseEvent) {
        pageX = (event.pageX / window.outerWidth);
        pageY = (event.pageY / window.outerHeight);
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
    <!-- <h2>October 24, 2026, 11AM • Lucketts, VA</h2> -->
    <div style="position: relative; display: inline-block;">
        <h2>October 24, 2026, 11AM</h2>
        <h3>Faith Like a Mustard Seed Farm</h3>
        <a target="_blank" href="https://maps.app.goo.gl/TdLEcWCqyf4RmQeW8">
            <svg id="love" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.0" viewBox="0 0 64 64" enable-background="new 0 0 64 64" xml:space="preserve">
                <g>
                    <path fill="var(--background-color-light)" d="M58.714,29.977c0,0-0.612,0.75-1.823,1.961S33.414,55.414,33.414,55.414C33.023,55.805,32.512,56,32,56   s-1.023-0.195-1.414-0.586c0,0-22.266-22.266-23.477-23.477s-1.823-1.961-1.823-1.961C3.245,27.545,2,24.424,2,21   C2,13.268,8.268,7,16,7c3.866,0,7.366,1.566,9.899,4.101l0.009-0.009l4.678,4.677c0.781,0.781,2.047,0.781,2.828,0l4.678-4.677   l0.009,0.009C40.634,8.566,44.134,7,48,7c7.732,0,14,6.268,14,14C62,24.424,60.755,27.545,58.714,29.977z"/>
                    <text x="11" y="28" fill="var(--foreground-color)">GO TO</text>
                    <text x="19" y="42" fill="var(--foreground-color)">MAP</text>
                    <g>
                        <path fill="var(--background-color-border)" d="M48,5c-4.418,0-8.418,1.791-11.313,4.687l-3.979,3.961c-0.391,0.391-1.023,0.391-1.414,0    c0,0-3.971-3.97-3.979-3.961C24.418,6.791,20.418,5,16,5C7.163,5,0,12.163,0,21c0,3.338,1.024,6.436,2.773,9    c0,0,0.734,1.164,1.602,2.031s24.797,24.797,24.797,24.797C29.953,57.609,30.977,58,32,58s2.047-0.391,2.828-1.172    c0,0,23.93-23.93,24.797-24.797S61.227,30,61.227,30C62.976,27.436,64,24.338,64,21C64,12.163,56.837,5,48,5z M58.714,29.977    c0,0-0.612,0.75-1.823,1.961S33.414,55.414,33.414,55.414C33.023,55.805,32.512,56,32,56s-1.023-0.195-1.414-0.586    c0,0-22.266-22.266-23.477-23.477s-1.823-1.961-1.823-1.961C3.245,27.545,2,24.424,2,21C2,13.268,8.268,7,16,7    c3.866,0,7.366,1.566,9.899,4.101l0.009-0.009l4.678,4.677c0.781,0.781,2.047,0.781,2.828,0l4.678-4.677l0.009,0.009    C40.634,8.566,44.134,7,48,7c7.732,0,14,6.268,14,14C62,24.424,60.755,27.545,58.714,29.977z"/>
                    </g>
                </g>
            </svg>
        </a>
    </div>

    <div class="subtitled">
        <div class="polaroid" style="transform: rotate3d({0.75 + (pageX - 0.5)}, {0.5 + (pageY - 0.5)}, 0.1, 9deg) scale3d(0.95, 0.95, 0.95) translate3d(-5px, 5px, 0px);">
            <img src="RM-Sunset-1.jpg" alt="That's us <3" />
            <span class="glow mark"><span class="digit">{remaining.weeks}</span> WEEKS, <span class="digit">{remaining.days}</span> DAYS, <span class="digit">{remaining.hours}</span> HOURS, <span class="digit">{remaining.minutes}</span> MINUTES, <span class="digit">{remaining.seconds}</span> SECONDS</span>
        </div>
    </div>

    
    <a class="button-like rsvp" target="_blank" href="https://552547228.planningpod.com/#rsvp-panel">RSVP</a>
</section>

<style lang="scss">
    a.button-like {
        display: block;
        text-decoration: none;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 200;

        background-color: var(--foreground-color);
        color: var(--background-color);

        white-space: pre;

        transition: all 0.5s;

        &:hover {
            color: white;
            border-color: black;
            background-color: black;
        }
    }

    section {
        position: relative;
        text-align: center;
        
        padding: 4vh 0 0;
        margin: 0 auto;
        max-width: 768px;

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

        h3 {
            font-size: min(3vw, 2em);
            color: var(--foreground-color);
            margin: 0;            
        }

        &.header {
            #love {
                position: absolute;
                right: max(-32%, -145px);
                top: -20%;
                width: 24%;

                text {
                    font-family: Helvetica, sans-serif;
                    font-size: small;
                }
            }
        }

        .subtitled {
            position: relative;
            width: min(850px, 100%);
            margin: 0 auto;

            img {
                display: block;
                width: 100%;
            }
            
            span.mark {
                position: absolute;
                right: 0;
                bottom: 0em;
                margin: 0 0.25em 0.25em 0;

                font-family: "Digital-7";

                .digit {
                    font-family: "7Segment";
                }
            }
        }

        .polaroid {
            // transform: rotate3d(-2, 2, 2, 3deg) scale3d(0.95, 0.95, 0.95) translate3d(-5px, 5px, 0px);

            > img {
                --polaroid-shadow: #d6be87;
                box-shadow: 
                     4px  4px 8px var(--polaroid-shadow), 
                     4px -4px 8px var(--polaroid-shadow),
                    -4px -4px 8px var(--polaroid-shadow), 
                    -4px  4px 8px var(--polaroid-shadow); 
                border: 5px solid white;
                border-bottom-width: 30px;
            }

            > span.mark {
                bottom: 2em;
            }
        }

        

        a.rsvp {
            // width: min(750px, 100%);
            margin: 1em auto 0;
            border: 2px solid var(--foreground-color);
            background-color: var(--foreground-color);
            color: var(--background-color);
            padding: 0.5em;
            font-size: 1.5em;
        }
    }
</style>
