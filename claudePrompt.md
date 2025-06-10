Do everything in the cadre of aristotelian logic. Remember to phrase or convert any detected proposition in extremely strict logical form.
Analyse the given text and determine whether there is a deductive argument. 
If there is no argument, return "no argument detected."
Otherwise, determine the type of argument present. It can be simple or compound. Simple arguments are based on two simple propositions and one conclusion. Compound propositions consist of two simple (categorical) propositionsjoined and related by one of three conjunctions: (1) " i f . . . then . . ( T h e s e are hypothetical or conditional propositions,and syllogisms that begin with them are called hypothetical syllogisms.)(2) "either . . . o r . . . " (These are disjunctive propositions, and syllogismsthat begin with them are called disjunctive syllogisms.)(3) "both ... and ..." or "not both ... and ..(These are conjunctive propositions, and syllogisms that begin with them are called conjunctive syllo- gisms.)
Determine what the terms are. 

Define each term according to the following rules using the context of the text. 
A definition should be coextensive with the thing defined: neither too broad nor too narrow. (This is the most important rule, and the hard- est to obey. It concerns the extension of the term rather than the com- prehension.)
A definition should be clear, not obscure.
A definition should be literal, not metaphorical.
A definition should be brief, not long.
A definition should be positive, not negative, if possible. (Only negative realities call for negative definitions.)
A definition should not be circular. (The term defined cannot appear in the definition.)

Determine what the premises are. Determine what kind of premises they are based on the following rules. 
simple propositions, with one subject and one predicate. These are called categorical propositions in logic. There are also compound propositions, which are made of two or more simple propositions - e.g. "If apples are fruits, then apples are not vegetables" or "Either apples are fruits or apples are vegetables," or "Apples are fruits and tomatoes are vegeta- bles." But in these compound propositions too, each simple proposition within the compound proposition must always have a subject and a predicate. We will study compound propositions a few chapters later. There are three kinds: hypo- thetical ("if. . . then . . ."), disjunctive ("either . . . or . . ."), and conjunctive ("both . . . and . . ." or "not both . . . and . . .").
Linguistic expressions can be (I) less than sentences (words or phrases), (II) sentences, or (III) more than sentences (discourses composed of a number of sentences).
Sentences are divided into (A) declarative sentences, which are proposi- tions, and (B) other kinds of sentences, which are not propositions: interroga- tive, imperative, exclamatory, and performative sentences.
Propositions are divided into (1) simple (also callcd "categorical") proposi- tions and
(2) compound propositions.
Simple propositions will be divided (in the next chapter) into four kinds: (a) universal affirmative propositions, (b) universal negative propositions, (c) particular affirmative propositions, and (d) particular negative propositions.
 142
Compound propositions will be divided into (a) hypothetical ("if... then...") propositions, (b) disjunctive ("either... or...") propositions, and (c) conjunc- tive ("both .. . and . . o r "not both ... and ...") propositions.
The following outline should help to orient us, like a wide-ranging road map:
Linguistic expressions:
I. Less than sentences (terms)
II. Sentences
A. Declarative sentences (propositions)
1. Simple (categorical)
(a) Universal affirmative (b) Universal negative (c) Particular affirmative (d) Particular negative
2. Compound
(a) Hypothetical
(b) Disjunctive
(c) Conjunctive

If it is a simple deductive arugment, the kind that follows the form all men are mortal, socrates is a man, therefore, socrates is mortal, then use the following rules to determine whether it is valid. 
Rule 1: A syllogism must have three and only three terms. The usual vio- lation of this rule is called The Fallacy of Four Terms. Rule 2: A syllogism must have three and only three propositions. There is no named fallacy for the violation of this rule. Rule 3: The middle term must be distributed at least once. The violation of this rule is called The Fallacy of Undistributed Middle. Rule 4: No term that is undistributed in the premise may be distributed in the conclusion. The violation of this rule is called The Fallacy of Illicit Minor or The Fallacy of Illicit Major, depending on whether it is the minor term or the major term that contains the fallacy. Rule 5: No syllogism can have two negative premises. The fallacy here is called simply the fallacy of Two Negative Premises. Rule 6: If one premise is negative, the conclusion must be negative; and if the conclusion is negative, one premise must be negative. 

If it is a compound hypothetical argument, evaluate it based on "Affirming the Antecedent" and "Denying the Consequent'' are the two valid forms of hypothetical syllogisms. "Affirming the Consequent" and "Denying the Antecedent" are the two invalid forms, the two fallacies.

If it is a compound disjunctive argument, However, there are really only two forms, since p and q are reversible and interchangeable in a disjunctive proposition, as they are not in a hypothetical proposition. "Either p or q" says exactly the same thing as "either q or p." But "if p then q" does not at all say the same thing as "if q then p."
The two forms, then, are the affirmative second premise ((1) or (2) above) and the negative second premise ((3) or (4) above).
The affirmative form is invalid and the negative form is valid.

If it is a compound conjunctive argument, So the only conclusion we can validly prove with a conjunctive syllogism is a negative one, just as the only conclusion we can validly prove with a disjunc- tive syllogism is an affirmative one. This is a very practical point to keep in mind when constructing such arguments as well as evaluating them.

Determine whether any of the premises are based on informal fallacies. 

Now return a json file. If it is a simple deductive argument return the following keys

major_term: the predicate of the conclusion
minor_term: the subject of the conclusion
middle_term: the term in both premises
def_maj: definition of the major term
def_min: definition of the minor term
def_mid: definition of the middle term
major_premise: the premise with the major term
minor_premise: the premise with the minor term
conclusion: what is trying to be proved
validity: whether it is valid

if it is a hypothetical compound argument return a similar json file but change the term keys to fit the terms of that argument, and give premises their names. 
same for conjunctive and disjunctive. 
