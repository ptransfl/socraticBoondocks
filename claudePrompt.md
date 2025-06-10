# Aristotelian Logic Analysis Instructions

## TASK OVERVIEW
Analyze the given text for deductive arguments using strict Aristotelian logical principles. Convert all propositions into formal logical statements and return structured JSON output.

## STEP-BY-STEP PROCESS

### STEP 1: ARGUMENT DETECTION
Read the entire text and determine: **Is there a deductive argument present?**
- Look for premises that lead to a conclusion
- Ignore purely descriptive, narrative, or explanatory passages
- If NO argument is found, skip to STEP 7 (JSON output) with `"argument_present": "no"`

### STEP 2: ARGUMENT TYPE CLASSIFICATION
Use this **DECISION TREE** in exact order of priority:

**Priority 1 - CONJUNCTIVE ARGUMENTS:**
- Text contains: "not both X and Y" OR "both X and Y" (asserting joint truth/falsehood)
- Phrases like: "nothing can be both", "it cannot be that both", "neither X nor Y"
- **→ CLASSIFY AS CONJUNCTIVE**

**Priority 2 - HYPOTHETICAL ARGUMENTS:**
- Text contains: "if X then Y", "when X then Y", "given X, therefore Y"
- Causal relationships: "because X, therefore Y", "X leads to Y", "X implies Y"
- **→ CLASSIFY AS HYPOTHETICAL**

**Priority 3 - DISJUNCTIVE ARGUMENTS:**
- Text contains: "either X or Y", "X or Y" (exclusive sense), "X unless Y"
- Presents mutually exclusive alternatives
- **→ CLASSIFY AS DISJUNCTIVE**

**Priority 4 - SIMPLE CATEGORICAL ARGUMENTS:**
- Only if NO compound connectives are present
- Standard syllogistic form with three terms across two premises
- **→ CLASSIFY AS SIMPLE**

#### For HYPOTHETICAL Arguments:
- **VALID FORMS ONLY**:
  - **Affirming the Antecedent (Modus Ponens)**: If P then Q; P is true; Therefore Q
  - **Denying the Consequent (Modus Tollens)**: If P then Q; Q is false; Therefore P is false
- **INVALID FORMS**:
  - **Affirming the Consequent**: If P then Q; Q is true; Therefore P (INVALID)
  - **Denying the Antecedent**: If P then Q; P is false; Therefore Q is false (INVALID)
- **CRITICAL**: A hypothetical argument MUST have a second premise that either affirms the antecedent OR denies the consequent. Without this second premise, there is NO deductive argument present.

#### For DISJUNCTIVE Arguments:
- **VALID FORMS ONLY**:
  - **Denying One Alternative**: Either P or Q; Not P; Therefore Q
  - **Denying One Alternative**: Either P or Q; Not Q; Therefore P
- **INVALID FORMS**:
  - **Affirming One Alternative**: Either P or Q; P is true; Therefore not Q (INVALID - unless exclusive disjunction is clearly stated)
- **CRITICAL**: A disjunctive argument MUST have a second premise that denies one of the alternatives. Without this negative second premise, there is NO deductive argument present.

#### For CONJUNCTIVE Arguments:
- **VALID FORMS ONLY**:
  - **Denying the Conjunction**: Not both P and Q; P is true; Therefore not Q
  - **Denying the Conjunction**: Not both P and Q; Q is true; Therefore not P
- **INVALID FORMS**:
  - **Affirming from Conjunction**: Both P and Q; Therefore P (INVALID - this is not deductive reasoning)
  - **Affirming the Conjunction**: Not both P and Q; Not P; Therefore Q (INVALID)
- **CRITICAL**: A conjunctive argument MUST start with a negative conjunctive premise ("not both P and Q") and have a second premise that affirms one alternative to deny the other. Positive conjunctions ("both P and Q") do not form valid deductive arguments.

### STEP 3: STRUCTURAL ANALYSIS

#### For SIMPLE Arguments:
- Identify exactly three terms (no more, no fewer)
- Locate major premise (contains major term)
- Locate minor premise (contains minor term)
- Identify conclusion
- Find any implicit premises

#### For COMPOUND Arguments:
- Identify the compound proposition (if-then, either-or, not both-and)
- Locate the second premise
- Identify conclusion
- Note any implicit elements

### STEP 4: TERM DEFINITION
Define each key term using these rules:
1. **Coextensive**: Neither too broad nor too narrow
2. **Clear**: Not obscure or vague
3. **Literal**: Not metaphorical
4. **Brief**: 1-2 sentences maximum
5. **Positive**: Avoid negative definitions when possible
6. **Non-circular**: Don't use the term being defined

### STEP 5: VALIDITY ASSESSMENT

#### For SIMPLE Arguments - Check These Rules:
1. Must have exactly three terms (Fallacy of Four Terms)
2. Must have exactly three propositions
3. Middle term must be distributed at least once (Undistributed Middle)
4. No term undistributed in premise may be distributed in conclusion (Illicit Major/Minor)
5. Cannot have two negative premises
6. If one premise is negative, conclusion must be negative

#### For HYPOTHETICAL Arguments:
- **VALID**: Affirming the Antecedent, Denying the Consequent
- **INVALID**: Affirming the Consequent, Denying the Antecedent

#### For DISJUNCTIVE Arguments:
- **VALID**: Negative second premise (denying one alternative)
- **INVALID**: Affirmative second premise (affirming one alternative)

#### For CONJUNCTIVE Arguments:
- **VALID**: Only when conclusion is negative
- **INVALID**: When attempting to prove affirmative conclusion

### STEP 6: FALLACY DETECTION
Check for these common informal fallacies in premises:
1. Fallacies of language
A. Equivocation 71 B. Amphiboly 74 C. Accent 75 D. Slanting 76 E. Slogans 78 F. Hyperbole 78 G. "Straw Man" 79
2. Fallacies of Diversion
A. Ad hominem (The Appeal to the Person), including 80
"Poisoning the Well,"
Tu quoque ("You Too"), and
"The Genetic Fallacy"
B. Ad verecundiam (The Appeal to [Illegitimate] Authority) 82 C. Ad baculum (The Appeal to Force) 83 D. Ad misericordiam (The Appeal to Pity) 84 E. Ad ignominiam (The Appeal to Shame) 84 F. Adpopulum (The Appeal to the Masses), including 85
Flattery (or "The Appeal to the Gallery"), Identification ("I'm one of you!"), "Everybody Docs It,"
"The Polls Say,"
The Appeal to Prejudice, "Snob Appeal," and
"The Big Lie"
86
G. Ad ignorantiam (The Appeal to Ignorance)
 70
lit. MATERIAL FALLACIES
3. Fallacies of Oversimplification
A. Die to simp liciter 86 B. "Special Case" 87 C. Composition 87 D. Division 88 E. "The Black-and-White Fallacy" 89 F. Quoting out of Context 90 G. Stereotyping 91
4. Fallacies of Argumentation
A. Non sequitur ("It Does Not Follow") 92 B. Ignoratio Elenchi (Irrelevant Conclusion, or "Ignorance
of the Chain" connecting premises and conclusion) 94 C. Petitio principii ("Begging the Question") 94 D. "Complex Question" 95 E. Arguing in a Circle 95 F. Contradictory Premises 97 G. False Assumption 99
5. Fallacies of Induction
A. Hasty Generalization 100 B. Post hoc, ergo propter hoc ("After this, therefore caused by this") 100 C. Hypothesis Contrary to Fact 101 D. False Analogy 102 E. Argument from Silence 103 F. Selective Evidence 103 G. Slanting the Question 104
6. Procedural Fallacies
A. "Refuting" an Argument by Refuting its Conclusion 104 B. Assuming that Refuting an Argument Disproves Its
Conclusion 105 C. Ignoring an Argument 106 D. Substituting Explanations for Proof 106 E. Answering Another Argument than the One Given 107 F. Shifting the Burden of Proof 108 G. W inning the Argument but Losing the Arguer, or Vice Versa 108
7. Metaphysical Fallacies
A. Reductionism or "Nothing Buttery" (especially, Confusing
Form with Matter) 109 B. The Fallacy of Accident (Confusing the Accidental
with the Essential) 110 C. Confusing Quantity with Quality
D. The Fallacy of Misplaced Concreteness (Confusing the
Abstract with the Concrete) 111 E. Confusing the Logical, Psychological, and Physical "Because" 112 F. The Existential Fallacy (Confusing Essencc and Existence) 112 G. Confusing the Natural with the Common 113

### STEP 7: JSON OUTPUT

## OUTPUT FORMATS

### If NO Argument Present:
```json
{
  "argument_present": "no"
}
```

### If SIMPLE Argument Present:
```json
{
  "argument_present": "yes",
  "argument_type": "simple",
  "major_term": "[predicate of conclusion]",
  "minor_term": "[subject of conclusion]", 
  "middle_term": "[term appearing in both premises]",
  "def_maj": "[definition of major term]",
  "def_min": "[definition of minor term]",
  "def_mid": "[definition of middle term]",
  "major_premise": "[premise containing major term]",
  "minor_premise": "[premise containing minor term]",
  "conclusion": "[what is being proved]",
  "validity": "[valid/invalid with reason]"
   "informal": "any possible informal fallacies"
}
```

### If HYPOTHETICAL Argument Present:
```json
{
  "argument_present": "yes",
  "argument_type": "compound",
  "antecedent": "[the 'if' part]",
  "consequent": "[the 'then' part]",
  "def_ant": "[definition of antecedent]",
  "def_con": "[definition of consequent]",
  "hypothetical": "[the if-then premise]",
  "second_premise": "[the other premise]",
  "conclusion": "[what is being proved]",
  "validity": "[valid/invalid with reason]"
  "informal": "any possible informal fallacies"
}
```

### If DISJUNCTIVE Argument Present:
```json
{
  "argument_present": "yes",
  "argument_type": "compound",
  "first_term": "[the 'either' part]",
  "second_term": "[the 'or' part]",
  "def_first": "[definition of first term]",
  "def_second": "[definition of second term]",
  "disjunctive": "[the either-or premise]",
  "second_premise": "[the other premise]",
  "conclusion": "[what is being proved]",
  "validity": "[valid/invalid with reason]"
   "informal": "any possible informal fallacies"
}
```

### If CONJUNCTIVE Argument Present:
```json
{
  "argument_present": "yes",
  "argument_type": "compound",
  "first_term": "[first term in conjunction]",
  "second_term": "[second term in conjunction]",
  "def_first": "[definition of first term]",
  "def_second": "[definition of second term]",
  "conjunctive": "[the not both-and or both-and premise]",
  "second_premise": "[the other premise]",
  "conclusion": "[what is being proved]",
  "validity": "[valid/invalid with reason]"
   "informal": "any possible informal fallacies"
}
```

## MULTIPLE ARGUMENTS
If multiple arguments are present, number them:
- First argument: standard keys
- Second argument: add "1" to each key (e.g., "major_term1", "minor_term1")
- Third argument: add "2" to each key (e.g., "major_term2", "minor_term2")

## CRITICAL RULES
1. **Always convert propositions to strict logical form** before analysis
2. **Follow the decision tree priority order** - don't default to simple when compound elements exist
3. **Mark implicit premises clearly** as [IMPLICIT] in output
4. **One argument type per analysis** - choose the primary logical structure
5. **Definitions must be contextual** to the argument being analyzed
6. **Validity assessment must reference specific logical rules**

## ERROR HANDLING
- **Ambiguous terms**: Define based on argument context
- **Mixed structures**: Classify by primary logical connective
- **Unclear premises**: Make reasonable inferences and mark as [IMPLICIT]
- **Multiple valid interpretations**: Choose the strongest logical reading
