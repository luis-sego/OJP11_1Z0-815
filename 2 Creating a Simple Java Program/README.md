# 2 Creating a Simple Java Program

## Summary

In this section we will review the requeriments for executing a simple Java program as follows:
The structure of the source code must meet these minimum requirements:
- The name of the class which has the main method doesn't matter.
- The accesss modifier of the class does not matter - in the case of a class you can define it as 'public' or use the default modifier.
- If you do declare the class public, you must name the file the same as  the class name with a .java extension.
- The number of classes in the file does not matter -  you can define as many classes as you want in a single file, but only one can be public, and the filename must be the same as the public class.
- When you compile the file, the compiler will create a separate .class file for each defined class.
- You can define a main method in any or all of the classes.
- The main method of the class where your application starts must have the signature: **public static void main(String[] args)**
- From Java's point of view these signatures are equivalent for the JVM to execute the main method:
  - public static void main(String... args);
  - public static void main(String args[]) throws Exception;
- You can execute code in the following ways:
    - launch a single source-file program
        - java [options] source-file [args...]
    - To launch a class file either in a directory or a jar file
        - java [options] mainclass [args...]
    - launch the main  class in a JAR file
        - java [options] -jar jarfile [args...]
    - Executing a class in a module (which we'll discuss in a later video)
        - java [options] --module module[/mainclass] [args...]
        - java [options] -m module[/mainclass] [args...]
- You can pss data on the command line to your application as a space delimited set of strings. These are the String[] args represented by the parameter of main.

## Main Java Tools

The following table shows Main Tools to create and build applications.

| Tool     |          Purpose           | Some common option |
| -------- | :------------------------: | -----------------: |
| java     | Launch a Java application. | **--class-path, -classpath, -cp** (parameter is a semicolon (;) separated list of directories, JAR archives and ZIP archives to search for class files).<br />**-verbose:class** (Displays information about each loaded class)<br />**-verbose:gc** (Displays infromation about each garbage collection (GC) event).|
| javac     | Read Java class and interfaces definitions and compile them into bytecode and class files. | **-d** (Sets the destination directory for class files).<br />**-g** (Generates all debbuging information).<br />**-g:[lines, vars, source]** (Generates only the kinds of debbuging information especified by the comma separated list of keywords).<br />**-g:none** (Doesn't generate debbugin information).<br />**-verbose** (Outputs messages about what the compiler is doing). |
| jar       | Create an archive for classes and resources, and to manipulate or restore individual classes or resources form an archive. | **-c, --create** (Creates the archive).<br />**-C** (Changes the specified directory and includes the files specified at the end of the command line).<br />**-f, --file**(Specifies the archive file name).<br />**-m, --manifest** (Includes the manifest information from teh giveb manifest file). |
| javap     | Disassemble one or more class files. | **-c** (Prints dissasemble code, for example, the instructions that compile the Java bytecodes, for each of the methods in the class). |
| javadoc   | Generate HTML pages of API documentation form Java source files. | Usage not part of first exam. |
| jlink     | Assemble and optimize a set of modules and their dependecies into a custom runtime image. | Usage not part of first exam. |
| jmod      | Create JMOD files and list the content of existing JMOD files. | Usage not part of first exam. |
| jdeps     | Launch the Java class dependency analyzer. | Discussed in Modules section. |
| jdeprscan | Static analysis tool that scans a jar file (or some other aggregation of class files) for uses of deprecated API elemnts. | Discussed in Modules section. |

## Tha Main Method Singature

If you want the class to be executable, the Java Virtual Machine will look for a main method that is both public and static. Removing either of these modifiers means you will no longer have to execute class.

Also, the method signature, the name ('main') and its parameters (String[]) must match.

Here is a table showing the valid method declaration in Java. For all declarations:
- public and static modifiers are both required.
- return type is always void.

| Point to remember | Code Samples |
| -------- | :------------------------: |
| The keywords public and static can be in any order but both are mandatory. | public static void main(String[] args) {}<br /static public void main(String[] args) {} |
| Other modifiers are allowed, these include final, strictfp, synchronized in any order, in any combination. | public final static void main(String[] args) {}<br /public final strictfp static void main(String[] args) {}<br /public final strictfp synchronized static void main(String[] args) {}<br /public final static synchronized strictfp void main(String[] args) {} |
| The parameter of the main method can take the var-args syntax as well as all valid array syntax. | public static void main(String[] args) {}<br /public static void main(String args[]) {}<br /public static void main(String []args) {}<br /public static void main(String... args) {}<br /public static void main(String...args) {} //no space after elipsis |
| The parameter of the main method can be declared final. | public static void main(final String[] args) {}<br /|
| The parameter of the main method can be named anything. | public static void main(String[] arguments) {}<br /public static void main(String[] stuff) {}<br /public static void main(String[] vars) {}<br /public static void main(String[] ARGs) {}<br /|
| The method can declare a throws clause for unhandled exception of any kind. | public static void main(String[] args) throws Exception {}<br /public static void main(String[] args) throws RuntimeException {}<br /public static void main(String[] args) throws Throwable {}<br /public static void main(String[] args) throws Error {}<br / |