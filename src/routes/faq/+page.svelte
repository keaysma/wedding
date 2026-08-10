<ul class="faqs">
    <li>
        <details>
            <summary>
                Where is the wedding?
            </summary>
            <p>
                Faith Like a Mustard Seed Farm.
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                What time does the ceremony start?
            </summary>
            <p>
                The ceremony will start at 3:30PM (double check)
            </p>
        </details>
    </li>
    <li>
        <details>
            <summary>
                Where can I park my car?
            </summary>
            <p>
                The venue provides enough parking for 60 vehicles (double check)
            </p>
        </details>
    </li>
</ul>

<style lang="scss">
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
        }
  
        &[open]::details-content {
            height:auto;
        }

        summary {
            font-size: larger;

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
