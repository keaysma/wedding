<ul class="faqs">
    <li id="return-home">
        <a href="/">☜ Back to Homepage</a>
    </li>
    <li>
        <details>
            <summary>
                When should I RSVP by?
            </summary>
            <!--I picked that date off of the top of my head btw-->
            <p>
                The sooner the better! Please get back to us by October 7th.
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                Where is the wedding?
            </summary>
            <p>
                The wedding ceremony and reception is at Faith Like a Mustard Seed Farm. <br>
                Address: 42906 Lucketts Rd, Leesburg, VA 20176 <br>
                <a href="https://maps.app.goo.gl/ynDBXuKPZ8QjdLYH6">Google Maps Link</a>
                <br><br>
                The ceremoney will be held outside facing the countryside, weather permitting. The reception will be held in the barn. If there is rain the ceremony will also be held in the barn.
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                What time does the ceremony start?
            </summary>
            <p>
                The ceremony will start at 3:30PM. We recommend that guests aim to arrive at the venue at closer to 3PM to 3:15PM to say hello to other guests and grab a seat!
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                Where can I park my car?
            </summary>
            <p>
                The venue provides parking space on site, its right near the horse barn, and we will have signage to direct you to the parking.
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                Are there hotel room blocks?
            </summary>
            <p>
                We have a room block at the Washington Dulles Airport Mariot Hotel, you can book your reservation right here: <a target="_blank" href="https://www.marriott.com/event-reservations/reservation-link.mi?id=1789055572399&key=GRP&app=resvlink">link to hotel block</a>.
                <br/>
                <br/>
                Hotel reservations with the room block must be made by <b>September 25</b>!
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                What is the dress code?
            </summary>
            <p>
                Cocktail hour dress code: semi-formal wear like dresses, suit jackets and slacks, but, not too formal.
            </p>
        </details>
    </li>
</ul>
<img id="gremlin" src="/sheeta.png" />

<style lang="scss">
#return-home {
    padding-bottom: 1em;

    a {
        font-size: 1.5em;
        text-decoration: none;
    }
}

#gremlin {
    position: fixed;
    width: 12em;
    transform: ScaleX(-1);
    opacity: 0.33;
    right: 2em;
    bottom: 0.5em;
}

ul.faqs {
    list-style: none;

    width: 100%;
    padding: 1em;

    details {
        interpolate-size: allow-keywords;

        color: var(--background-color);
        background-color: var(--foreground-color);

        margin: 0.25em 0;
        padding: 0.5em 0.5em 0.5em;

        font-size: 1.5em;
  
        &::details-content {
            transition:
                height 0.25s,
                content-visibility 0.5s allow-discrete;
            overflow: hidden;
            height: 0;
            font-family: "Mooli", sans-serif;
        }
  
        &[open]::details-content {
            height:auto;
        }

        summary {
            font-size: larger;

            cursor: pointer;

            &::marker {
                // content: "♥︎ ";
                content: "";
            }

            &::before {
                content: "︎︎♥︎";
                display: inline-block;
                transition: transform 0.2s ease;
                margin-right: 5px;
            }
        }

        /*
        &[open] summary::marker {
            content: "❥ ";
        }
        */

        &[open] summary::before {
            transform: rotate(-90deg);
            color: #e97687;
        }

        p {
            margin: 0.25em 0.25em 0.25em 1.25em;

            font-size: smaller;
        }
    }
}
</style>
