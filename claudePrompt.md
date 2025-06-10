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
- **Equivocation**: Same word used with different meanings
- **Ad Hominem**: Attacking person instead of argument
- **False Dilemma**: Presenting only two options when more exist
- **Begging the Question**: Using conclusion as premise
- **Hasty Generalization**: Insufficient evidence for broad claim
- **Post Hoc**: Confusing correlation with causation

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
