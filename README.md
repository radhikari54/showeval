showeval
========

A JavaScript module to show the steps in evaluating an expression.

This module requires jQuery.

Example
-------

Create an HTML file in the same folder as JQuery and ShowEval's JavaScript files. You will need to set up a div element where the animation goes and (optionally) button elements for the "Next" and "Reset" features.

Create an array of strings. Each string is a step in the animation. Use the `{{` and `}}` braces to surround the part that should be replaced, followed by the replacement text also in `{{` and `}}`.

Pass this array of strings to the `SHOWEVAL.ShowEval()` function, along with the div element. The third `false` argument causes each step to replace the previous step. Passing `true` will show all the steps as the Next button is clicked.

    <script src="jquery-1.11.1.min.js"></script>
    <script src="showEval.js"></script>
    <button id="nextStep">Next Step</button>
    <button id="reset">Reset</button>
    <div id="showeval"></div>

    <script>

    $( "#nextStep").click(function() { s.evaluateStep(); });
    $( "#reset"   ).click(function() { s.reset(0); });

    $(document).ready(function() {
      // for each step, put the part to replaced in the first set of {{ }}, and the replacement text in the following {{ }}
      steps = ["''.join({{eggs}}{{['dogs', 'cats', 'moose']}}).upper().join(eggs)",
               "{{''.join(['dogs', 'cats', 'moose'])}}{{'dogscatsmoose'}}.upper().join(eggs)",
               "{{'dogscatsmoose'.upper()}}{{'DOGSCATSMOOSE'}}.join(eggs)",
               "'DOGSCATSMOOSE'.join({{eggs}}{{['dogs', 'cats', 'moose']}})",
               "{{'DOGSCATSMOOSE'.join(['dogs', 'cats', 'moose'])}}{{'dogsDOGSCATSMOOSEcatsDOGSCATSMOOSEmoose'}}"];
      s = new SHOWEVAL.ShowEval($('#showeval'), steps, false);
    });

    </script>
