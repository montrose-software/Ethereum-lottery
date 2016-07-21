# Ethereum-lottery
<h2>Ether RNG</h2>
<p>We aimed to leverage the unpredictability and lack of central control of the blockchain to create a random number generator that wouldn’t require any physical world interaction and could generate an unpredictable number. There were some tough requirements for that piece of code</p>
<ol>
 	<li>Number generated has to be unpredictable even if a precise time of a draw is known.</li>
 	<li>Number can’t be influenced in a predictable manner by anyone. Unfortunately some level of influence is still possible from the miners but this should offer impossible to predict results.</li>
</ol>
<p>The seed for the random number is created out of hashes of x number of previously mined blocks. The number of blocks as well as a starting block are provided as parameters to the function. The hashes of the selected blocks are then combined using a XOR function and projected on to the search space (also provided by the algorithm).</p>

<h2>Ether Lotto</h2>
<p>The lottery is fully transparent and every draw can be fully checked and validated by everyone with minimal effort. It is just a proof of concept program that can be further extended into a fully working ethereum based lottery engine. </p>

<h3>Routine:</h3>
<ol>
 	<li>Users bet by paying in an amount of ether that is equal or more than a bet value ( </span><span style="font-weight: 400">betValue</span><span style="font-weight: 400">).</li>
 	<li>If a user pays more than the bet value the number of lottery tickets will be incremented for this user until remainder &lt; bet value. The remainder is then return to the user.</li>
 	<li>In the current stage of development the ether lotto will collect the bets until the uniqueUsersThreshold is matched. A bet by a user that reaches that value starts the lottery. This can be easily modified to use a pot value. In future releases of Solidity when a scheduler is provided it can also be scheduled to run at certain time and date.</li>
 	<li>Meeting the above condition stops any further bets from being put and saves the latest block in ethereum block chain for use in the draw.</li>
 	<li>Draw is performed using “Ether RNG” program described above.</li>
 	<li>Ether RNG receives the latest block present when the draw was called as a start block parameter. Value of 6 to use 6 blocks into the past. And the number of bets as a search space.</li>
 	<li>After a draw is complete the lottery reads a payout address of a user that placed the lucky bet and send all the collected funds.</li>
</ol>

<h3>Known Problems:</h3>
<ol>
 	<li>After meeting the condition for triggering the lottery draw, the lottery should wait some time to ensure no malicious blocks were added and the draw is performed on the “longest chain”. The blockchain should take care of this validation automatically but time is required for the chain to grow.</li>
 	<li>Currently Solidity contains no way of scheduling events in time. Because of that the scheduling of a draw would have to be done externally which causes a loss of transparency. Solidity developers are working on a scheduler which should be present in a future version.</li>
 	<li>The Ether RNG used to draw the random number has not undergone the “Randomness tests” to confirm its correct number distribution. It may at the moment display a bias for some numbers.</li>
 	<li>The lottery can suffer from the 51% attack.</li>
</ol>

<p>The development of these programs has taught us a lot about the wonders of the blockchain as well as showed us many difficulties in developing for that immature platform. But it shows great potential for future. What these programs have shown was in fact not possible until now. This lottery has no owner, it requires no special commission and no trust. Currently everywhere in the world lotteries are controlled and heavily regulated by governments and being able to create one requires a lot of permissions and money. This lottery escapes that it can’t be regulated, stopped or controlled by any government or entity which on it’s own shows the potential of the blockchain based technologies to start a new era in programming.</p>


<p>Special thanks to <a href="https://twitter.com/tkorwin">Tomasz Korwin-Gajkowski<a> for guidence and advice</p>
