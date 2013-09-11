# Coding Conventions

This document provides guidelines for code formatting and documentation
to developers contributing to SilverStripe. It applies to:

 * All code in the framework/ and cms/ modules
 * Any modules maintained by SilverStripe

These conventions are also used by project teams at SilverStripe Ltd and we recommend them for use
as general-purpose coding conventions on your projects.

Coding standards are an important aspect for every software project,
and facilitate collaboration by making code more consistent and readable.

If you are unsure about a specific standard, imitate existing SilverStripe code.

## File Formatting

### Indentation

Always use hard tabs rather then spaces for indentation, with one tab per nesting level.

### Maximum Line Length

The target line length is 100 columns with tabs being treated as four columns, meaning developers 
should strive keep each line of their code under 80 columns where possible and practical. 

However, longer lines are acceptable in some circumstances. The maximum length of any line of PHP
code is 120 columns.

### Line Termination

Line termination follows the Unix text file convention. Lines must end with a single linefeed (LF) character. 
Linefeed characters are represented as ordinal 10, or hexadecimal 0x0A.

Note: Do not use carriage returns (CR) as is the convention in Apple OS's (0x0D) or the carriage return - 
linefeed combination (CRLF) as is standard for the Windows OS (0x0D, 0x0A).

## Language-specific conventions

 * [PHP](php)
 * [JavaScript](javascript)
   * [Entwine.js](entwine)
   
## Other imporant considerations

 * [Security](/topics/security)
 * [Topics: CSS](/topics/css)
 * [Reference: CMS Architecture](/reference/cms-archirecture)

 ## License

Parts of these coding conventions were adapted from [Zend Framework](http://framework.zend.com/manual/en/coding-standard.overview.html),
which are licensed under BSD (see [license](http://framework.zend.com/license)).