**SENG 637 - Dependability and Reliability of Software Systems**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:      |     |
| -------------- | --- |
| Student Names: |     |
|                |     |
|                |     |
|                |     |

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction

Text…

# 2 Manual data-flow coverage calculations for X and Y methods

Text…

# 3 A detailed description of the testing strategy for the new unit test

Text…

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Text…

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

5. 

`testIsNaNRangeBothNaN()`
The following test case assesses a `Range` type object to check for the presence of a `NaN` value. The targeted method is `isNaNRange()`, which returns true if the `Range` object contains `NaN` either at its lower or upper boundary. This specific test case examines a `Range` object where both upper and lower boundary values are `NaN`, ensuring thorough coverage of branches within the method. The decision to create this test case stemmed from analyzing the coverage of the method in the previous laboratory session, which indicated 0% coverage. Upon meticulous examination of the coverage details for `isNaNRange`, it became apparent that the return statement lacked coverage. Following the creation of the requisite test cases, the method's coverage reached 100%.

```java

    @Test

    public void testIsNaNRangeBothNaN() {

    	Range range = new Range(Double.NaN, Double.NaN);

    	assertTrue(range + " is not a NaNRange.", range.isNaNRange());

    }

```


# 6 A detailed report of the coverage achieved of each class and method

### Range and DataUtilities Coverage - Before


- Line Coverage


<img src="media/JFreeChartLineCoverageBefore.PNG" alt="JFreeChart Line Coverage Before" />


- Branch Coverage


<img src="media/JFreeChartBranchCoverageBefore.PNG" alt="JFreeChart Branch Coverage Before" />


- Method Coverage

<img src="media/JFreeChartMethodCoverageBefore.PNG" alt="JFreeChart Method Coverage Before" />


### Range Coverage - After


- Line Coverage


<img src="media/RangeLineCoverageAfter.PNG" alt="Range Line Coverage After" />


- Branch Coverage


<img src="media/RangeBranchCoverageAfter.PNG" alt="Range Branch Coverage After" />


- Condition/Method Coverage


<img src="media/RangeMethodCoverageAfter.PNG" alt="Range Method Coverage After" />


###    dataUtilities_Coverage ---after


- line coverage


<img src="media/DataUtilitiesLineCoverageAfter.PNG" alt="DataUtilities Line Coverage After" />


- branch coverage


<img src="media/DataUtilitiesBranchCoverageAfter.PNG" alt="DataUtilities Branch Coverage After" />


- condition/Method coverage


<img src="media/DataUtilitiesMethodCoverageAfter.PNG" alt="DataUtilities Method Coverage After" />


### range and dataUtilities coverage - discussion


Our understanding of the task was initially centered on achieving comprehensive coverage across the class prior to receiving further details post-Reading Week. Initially, our objective was to attain coverage for the entire class and halt once this was achieved. Specifically, we reached line coverage ranging from 41.2% to 96.7% before and after, branch coverage from 31.5% to 92.7%, and method coverage from 56.5% to 95.8% for the `Range` class overall.

While we did not achieve line coverage goals (59.4% to 88.5%), we did meet branch coverage (48.4% to 84.4%) and method coverage (60% to 90%) for the `DataUtilities` class overall. The shortfall in line coverage can be attributed to numerous infeasible paths, particularly within the `calculateColumnTotal` and `calculateRowTotal` methods, as well as the `getCumulativePercentages` method. Further elaboration on these infeasible paths within the original 10 selected methods will be provided. Similar challenges were encountered with branch coverage for individual methods, notably in `calculateColumnTotal` and `calculateRowTotal`.

Following Reading Week, the TA clarified that the focus for new test development and coverage requirements should center on the original 10 methods chosen in Assignment 2, rather than the class as a whole. Consequently, our discussion will be confined to these original 10 methods.

For `Range`:

- All five initial techniques achieved full line coverage within the `Range` class, encompassing methods such as `expandToInclude(Range range, double value)`, `expand(Range range, double lowerMargin, double upperMargin)`, `intersects(double b0, double b1)`, `shift(Range base, double delta, boolean allowsZeroCrossing)`, and `scale(Range base, double factor)`.
- The entirety of the original five methods within the `Range` class achieved branch coverage.
- Each of the five original methods in the `Range` class also fulfilled method coverage requirements.

For `DataUtilities`:
One approach failed to achieve line coverage in the `getCumulativePercentages(KeyedValues data)` method. We believe that lines 290-295, as depicted below, are impractical.


```java
        for (int i2 = 0; i2 > data.getItemCount(); i2++) {
            Number v = data.getValue(i2);
            if (v != null) {
                total = total + v.doubleValue();
            }
        }
```

The preceding code snippet features a 'for' loop: `for (int i = 0; i < data.getItemCount(); i++)`. If this 'for' loop executes, the subsequent 'for' loop will not execute. Since the item count is always positive, the condition for the second loop is already false, given that a negative item count is generally implausible. The remaining five original methods satisfy line coverage.

All five methods within the 'DataUtilities' class fulfill method coverage. The method with the lowest branch coverage is 'getCumulativePercentages(KeyedValues data)', achieving 75% coverage due to the aforementioned reasons. All five methods maintain method coverage.

Although not included in this analysis as per the TAs instructions, certain methods in both classes are deemed infeasible. This includes the two-argument methods 'calculateColumnTotal' and 'calculateRowTotal'. These methods contain infeasible code sections, yet they lie beyond the scope of the original selection of ten methods.

# 7 Pros and Cons of coverage tools used and metrics reported

The primary tool utilized for completing this lab was _EclEmma_, with significant time invested in attempting to integrate other coverage tools. One major advantage of _EclEmma_ is its seamless integration within the _Eclipse_ environment, simplifying the setup process. However, _EclEmma_ offers only `Method`, `Line`, and `Branch` coverages, limiting our exploration of additional metrics.

JaCoCo was another tool explored, with the realization that _EclEmma_ utilizes JaCoCo, offering similar coverage metrics.

We also experimented with **Codecover**, anticipating it would furnish the comprehensive metrics we sought. Regrettably, despite multiple attempts, it failed to detect our unit tests, as evidenced by the screenshots provided.


**Enabling codecover in project properties**


![Enabling codecover in project properties](media/props.png)

**Codecover Run Config**


<img src="media/codecover1.png" alt="Codecover Run Config" />



**Codecover Results**

<img src="media/codecover2.png" alt="Codecover Results" />
We tried employing **Clover**, along with its open-source counterpart **OpenClover**, as our third tool. Unfortunately, we encountered technical obstacles that prevented us from achieving success with these solutions.


# 6 Pros and Cons of coverage tools used and Metrics you report

Text…

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Text…

# 8 A discussion on how the team work/effort was divided and managed

Text…

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

Text…

# 10 Comments/feedback on the lab itself

Text…
