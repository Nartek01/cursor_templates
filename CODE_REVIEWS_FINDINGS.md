# Code Review Template

**Purpose:** Systematic code review framework for JavaScript/React/WordPress/SCSS projects  
**Version:** 1.0  
**Last Updated:** October 16, 2025

---

## How to Use This Template

1. **Copy this template** for each code review session
2. **Fill in metadata** section below with review specifics
3. **Create milestones** for each feature/component being reviewed
4. **Apply passing criteria** relevant to your tech stack
5. **Document issues** using the severity framework (Critical/Moderate/Minor)
6. **Calculate quality score** using the scoring system at the end
7. **Prioritize fixes** in the recommendations section

---

## Review Metadata

**Review Date:** _[Insert date]_  
**Reviewed By:** _[Reviewer name(s)]_  
**Reviewed Files/Features:** _[List components, files, or features]_  
**Branch/Commit:** _[Git reference]_  
**Review Type:** _[Initial / Follow-up / Pre-merge / Post-release]_

---

## Milestone Template Structure

Use this structure for each feature/component being reviewed. Create as many milestones as needed.

### Milestone [N]: [Feature/Component Name] ✅

#### Files Reviewed
- `path/to/file1.js`
- `path/to/file2.scss`
- `path/to/file3.php`

#### ✅ Passing Criteria

Select and apply relevant criteria from the categories below:

**1. Naming Conventions** - PASS/FAIL
   - Consistent naming patterns across files
   - Clear, descriptive variable/function names
   - Follows project/framework conventions

**2. Pure Functions & Side Effects** - PASS/FAIL
   - Functions are pure where applicable
   - Side effects properly isolated and managed
   - No unintended global state mutations

**3. Memoization & Performance** - PASS/FAIL
   - Expensive computations properly memoized
   - Appropriate use of `useMemo`, `useCallback`, `memo()`
   - No unnecessary re-renders or recalculations

**4. Tree-shaking & Bundle Size** - PASS/FAIL
   - Clean named exports for tree-shaking
   - No unnecessary dependencies
   - Lazy loading applied where appropriate

**5. Framework Integration** - PASS/FAIL
   - Proper use of framework APIs
   - Follows framework best practices
   - Integrates with existing patterns

**6. Pattern Consistency** - PASS/FAIL
   - Matches existing codebase patterns
   - Similar features implemented similarly
   - No architectural inconsistencies

**7. Internationalization (i18n)** - PASS/FAIL
   - All user-facing strings wrapped in i18n functions
   - Proper translation keys and namespaces
   - No hard-coded text

**8. Accessibility (a11y)** - PASS/FAIL
   - Semantic HTML elements used
   - ARIA attributes where needed
   - Keyboard navigation support
   - Screen reader compatibility

**9. Error Handling** - PASS/FAIL
   - Proper error boundaries
   - Graceful degradation
   - User-friendly error messages

**10. Testing Coverage** - PASS/FAIL
   - Unit tests for business logic
   - Integration tests for workflows
   - Edge cases covered

#### ⚠️ Issues Found

Document all issues using the templates below. Adjust severity based on impact.

---

## Issue Templates

### 🔴 CRITICAL Issues

**Use for:** Bugs, breaking changes, security issues, data loss risks, accessibility violations

**Template:**

**[N]. [Issue Title]** - `filename.ext`
   - **Line(s):** [Line numbers or range]
   - **Issue:** [Clear description of the problem]
   - **Impact:** [How this affects users or system]
   - **Fix:** [Specific solution or code change needed]

**Examples:**
- State synchronization causing data loss
- Performance bottleneck blocking UI
- Security vulnerability (XSS, injection, etc.)
- Breaking API changes
- Memory leaks
- Critical accessibility violations (WCAG Level A)

---

### 🟡 MODERATE Issues

**Use for:** Maintainability concerns, technical debt, unclear code, missing documentation

**Template:**

**[N]. [Issue Title]** - `filename.ext`
   - **Line(s):** [Line numbers or range]
   - **Issue:** [Description of the concern]
   - **Risk:** [Potential future problems]
   - **Recommendation:** [Suggested improvement]

**Examples:**
- Magic numbers without explanation
- High CSS specificity
- Complex logic without comments
- Missing TypeScript types
- Duplicate code patterns
- Hard-to-maintain selectors
- Missing error handling

---

### 🟢 MINOR Issues

**Use for:** Style inconsistencies, small optimizations, nice-to-have improvements

**Template:**

**[N]. [Issue Title]** - `filename.ext`
   - **Line(s):** [Line numbers or range]
   - **Issue:** [Description of minor concern]
   - **Fix:** [Optional improvement]

**Examples:**
- Unnecessary code (unused variables, empty fragments)
- Style guide violations
- Missing JSDoc comments
- Potential micro-optimizations
- Inconsistent formatting

---

## Category-Specific Checklists

### JavaScript/React Review Checklist

- [ ] Component structure follows project patterns
- [ ] Hooks used correctly (dependencies, order)
- [ ] Props properly typed/validated
- [ ] State management appropriate for complexity
- [ ] Event handlers properly bound/memoized
- [ ] No console.log or debugging code
- [ ] Imports organized and clean
- [ ] No hardcoded URLs or config values

### CSS/SCSS Review Checklist

- [ ] Selectors have reasonable specificity
- [ ] No !important (or justified with comments)
- [ ] Responsive design implemented correctly
- [ ] CSS custom properties used for theming
- [ ] No magic numbers (or documented)
- [ ] Browser compatibility considered
- [ ] No duplicate styles
- [ ] Mobile-first approach followed

### WordPress-Specific Checklist

- [ ] Hooks and filters properly namespaced
- [ ] Translation functions used correctly
- [ ] Follows WordPress coding standards
- [ ] Proper escaping of output
- [ ] Sanitization of input
- [ ] Nonces used for forms
- [ ] Capability checks for admin functions
- [ ] Theme/plugin prefixes used

### Performance Checklist

- [ ] Database queries optimized
- [ ] No N+1 query problems
- [ ] Assets lazy-loaded where appropriate
- [ ] Images optimized and sized correctly
- [ ] Caching strategies implemented
- [ ] No blocking operations in render
- [ ] Bundle size within reasonable limits

---

## Example Milestone (Reference)

This example shows how to apply the template in practice.

### Milestone 1: Component Control System ✅

#### Files Reviewed
- `components/control-panel/index.js`
- `components/control-panel/control.js`
- `components/control-panel/utils.js`
- `styles/control-panel.scss`

#### ✅ Passing Criteria

1. **Naming Conventions** - PASS
   - Consistent use of `control-*` pattern
   - Clear function and variable names

2. **Pure Functions** - PASS
   - `utils.js` exports only pure data
   - No side effects detected

3. **Memoization** - PASS
   - `useMemo` correctly used for expensive operations
   - Proper dependency arrays

4. **Framework Integration** - PASS
   - Follows React best practices
   - Proper component composition

#### ⚠️ Issues Found

##### 🔴 CRITICAL

1. **Missing Value Synchronization** - `control.js`
   - **Line:** 25-30
   - **Issue:** Control doesn't show current selected value
   - **Impact:** User can't see current state after page reload
   - **Fix:** Add `value` prop derived from current state

##### 🟡 MODERATE

2. **Inline Styles Anti-pattern** - `control.js`
   - **Line:** 52
   - **Issue:** `style={{ border: '1px solid #949494' }}` should be in stylesheet
   - **Recommendation:** Extract to CSS class for maintainability

3. **Missing Documentation** - `utils.js`
   - **Lines:** All functions
   - **Issue:** No JSDoc comments explaining purpose
   - **Recommendation:** Add function documentation

##### 🟢 MINOR

4. **Unnecessary Fragment** - `index.js`
   - **Line:** 17-19
   - **Issue:** Fragment wrapping single element
   - **Fix:** Return element directly

---

## Summary Statistics

Use this section to tally findings:

- **Total Issues Found:** [N]
- **Critical (🔴):** [N]
- **Moderate (🟡):** [N]
- **Minor (🟢):** [N]

---

## Priority Recommendations

Organize fixes by priority level for the team.

### Must Fix Before Merge

List all critical issues and high-impact moderate issues:

1. **Issue #[N]:** [Brief description]
2. **Issue #[N]:** [Brief description]

### Should Fix Soon

List moderate issues and impactful minor issues:

1. **Issue #[N]:** [Brief description]
2. **Issue #[N]:** [Brief description]

### Nice to Have

List minor improvements and optimizations:

1. **Issue #[N]:** [Brief description]
2. **Issue #[N]:** [Brief description]

---

## Code Quality Score: [X]/100

**How to Score:**

Rate each category 0-100 based on:
- 90-100: Excellent, minor issues only
- 75-89: Good, some improvements needed
- 60-74: Acceptable, notable issues present
- 40-59: Needs work, significant issues
- 0-39: Major problems, requires refactor

**Breakdown:**

- **Functionality:** [X]/100 (Does it work as intended?)
- **Maintainability:** [X]/100 (Easy to understand and modify?)
- **Consistency:** [X]/100 (Follows project patterns?)
- **Performance:** [X]/100 (Optimized and efficient?)
- **Security:** [X]/100 (No vulnerabilities?)
- **Accessibility:** [X]/100 (Usable by everyone?)
- **Testing:** [X]/100 (Adequate test coverage?)
- **Documentation:** [X]/100 (Well documented?)

**Overall Assessment:** 

_[Write 2-3 sentences summarizing the review, highlighting major strengths and primary areas for improvement]_

---

## Review Notes

_[Optional section for additional context, discussions, or decisions made during review]_

---

## Follow-up Actions

- [ ] Schedule follow-up review for critical issues
- [ ] Create tickets for identified improvements
- [ ] Update team documentation if patterns need clarification
- [ ] Share findings with team
- [ ] Archive this review in project documentation

---

## Template Customization Guide

### For Different Project Types

**React Projects:**
- Add: Component lifecycle checks, hooks validation
- Focus: State management, re-render optimization

**WordPress Projects:**
- Add: Security (escaping, sanitization, nonces)
- Focus: Hook usage, translation, standards compliance

**Node.js/Backend:**
- Add: API design, error handling, database queries
- Focus: Performance, security, validation

**CSS/SCSS Projects:**
- Add: Design system compliance, responsive design
- Focus: Specificity, maintainability, performance

### Severity Guidelines

**Assign CRITICAL (🔴) when:**
- Breaks functionality for users
- Creates security vulnerabilities
- Causes data loss or corruption
- Violates WCAG Level A accessibility
- Introduces breaking changes without migration path

**Assign MODERATE (🟡) when:**
- Makes code harder to maintain
- Creates technical debt
- Misses best practices
- Lacks documentation
- Has minor performance impact

**Assign MINOR (🟢) when:**
- Style inconsistencies
- Could be slightly optimized
- Nice-to-have improvements
- Very low impact issues

---

**Template Version History:**
- v1.0 (2025-10-16): Initial generalized template
