# PROG5121 PoE — Part 1: Registration and Login Feature

A Java (Maven) application implementing the registration and login logic
for the Part 1 requirements of the Portfolio of Evidence, with JUnit 5
unit tests and GitHub Actions CI so the tests run automatically on every
push.

## Project structure

```
PoE_Part1/
├── pom.xml
├── README.md
├── .github/workflows/maven.yml     # runs `mvn test` on every push
└── src/
    ├── main/java/com/prog5121/poe/
    │   ├── Login.java              # registration + login logic
    │   └── Main.java               # console entry point (input/output)
    └── test/java/com/prog5121/poe/
        └── LoginTest.java          # JUnit 5 tests, using the exact
                                     # test data from the brief
```

## What each `Login` method does

| Method | Returns | Purpose |
|---|---|---|
| `checkUserName()` | `boolean` | Underscore present, ≤ 5 characters |
| `checkPasswordComplexity()` | `boolean` | ≥ 8 chars, capital, number, special char |
| `checkCellPhoneNumber()` | `boolean` | `+27` country code + ≤ 10-digit number |
| `registerUser()` | `String` | Registration outcome message |
| `loginUser(username, password)` | `boolean` | Checks credentials against the stored user |
| `returnLoginStatus(boolean)` | `String` | Welcome message or failure message |

## Running from the command line

```bash
mvn test      # compiles and runs all JUnit tests
mvn compile exec:java -Dexec.mainClass="com.prog5121.poe.Main"   # run the app
```


## Reference

The general structure of the cell-phone regular expression (an escaped
`+` combined with a bounded digit quantifier) was adapted from:

Baeldung (2023) *Validate Phone Numbers with Regex in Java*. Available
at: https://www.baeldung.com/java-regex-validate-phone-numbers
(Accessed: 15 September 2026).

This is also cited as a comment directly above `CELLPHONE_PATTERN` in
`Login.java`.
