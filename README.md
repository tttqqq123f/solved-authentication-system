Download Link: https://assignmentchef.com/product/solved-authentication-system
<br>
For security-minded professionals, it is important that only the appropriate people gain access to data in a computer system. This is called authentication. Once users gain entry, it is also important that they only see data related to their role in a computer system. This is called authorization. For the zoo, you will develop an authentication system that manages both authentication and authorization. You have been given a<strong>credentials file</strong> that contains credential information for authorized users. You have also been given three files, one for each role: <strong>zookeeper</strong>, <strong>veterinarian</strong>, and <strong>admin</strong>. Each role file describes the data the particular role should be authorized to access. Create an authentication system that does all of the following:

* Asks the user for a username

* Asks the user for a password

* Converts the password using a message digest five (MD5) hash

* It is not required that you write the MD5 from scratch. Use the code located in this document and follow the comments in it to perform this operation.

* Checks the credentials against the valid credentials provided in the credentials file.

* Use the hashed passwords in the second column; the third column contains the actual passwords for testing and the fourth row contains the role of each user.

* Limits failed attempts to three before notifying the user and exiting the program.

* Gives authenticated users access to the correct role file after successful authentication.

* The system information stored in the role file should be displayed. For example, if a zookeeper’s credentials is successfully authenticated, then the contents from the zookeeper file will be displayed. If an admin’s credentials is successfully authenticated, then the contents from the admin file will be displayed.

* Allows a user to log out.

* Stays on the credential screen until either a successful attempt has been made, three unsuccessful attempts have been made, or a user chooses to exit.

* You are allowed to add extra roles if you would like to see another type of user added to the system, but you may not remove any of the existing roles.

<strong><em>* Below is the Credentials file to be used.</em></strong>

<strong>* credentials file: This file must be used to validate user logins. This is the passwords and logins and who they belong too, they are seperated by one tab length in each column, from what I`m told</strong>

<pre class="ql-syntax"><span class="hljs-attribute">griffin</span>.keyes   108de81c31bf9c622f76876b74e9285f        <span class="hljs-string">"alphabet soup"</span> zookeeper<span class="hljs-attribute">rosario</span>.dawson  3e34baa4ee2ff767af8c120a496742b5        <span class="hljs-string">"animal doctor"</span> admin<span class="hljs-attribute">bernie</span>.gorilla  a584efafa8f9ea7fe5cf18442f32b07b        <span class="hljs-string">"secret password"</span>       veterinarian<span class="hljs-attribute">donald</span>.monkey   17b1b7d8a706696ed220bc414f729ad3        <span class="hljs-string">"M0nk3y business"</span>       zookeeper<span class="hljs-attribute">jerome</span>.grizzlybear      3adea92111e6307f8f2aae4721e77900        <span class="hljs-string">"grizzly1234"</span>   veterinarian<span class="hljs-attribute">bruce</span>.grizzlybear       0d107d09f5bbe40cade3de5c71e9e9b7        <span class="hljs-string">"letmein"</span>       admin</pre>

<strong><em>* Each user is part of a group. when they login the welcome screen for each group must have the following welcome screen. This is the Txt files that need to be read and displayed in the program</em></strong>

<strong><em>* These are the Txt files to use once the user logs in and is authenticated.</em></strong>

<strong>Zookeeper file:</strong>

<pre class="ql-syntax"><span class="hljs-attribute">Hello</span>, Zookeeper!<span class="hljs-attribute">As</span> zookeeper, you have access to <span class="hljs-literal">all</span> of the animals' information and their daily monitoring logs. This allows you to track their feeding habits, habitat conditions, and general welfare.<span class="hljs-attribute">Veterinarian</span> file:<span class="hljs-attribute">Hello</span>, Veterinarian!<span class="hljs-attribute">As</span> veterinarian, you have access to <span class="hljs-literal">all</span> of the animals' health records. This allows you to view each animal's medical history and current treatments/illnesses (if any), and to maintain a vaccination log.</pre>

<strong>Admin file:</strong>

<pre class="ql-syntax">Hello, System Admin!<span class="hljs-keyword">As</span> administrator, you have access to the zoo<span class="hljs-string">'s main computer system.  This allows you to monitor users in the system and their roles</span></pre>

<strong>* MD5 file: This is the actual MD5 file, just copied into this document.</strong>

import java.security.MessageDigest;

public class MD5Digest {

public static void main(String[] args) throws Exception {




//Copy and paste this section of code

String original = “letmein”; //Replace “password” with the actual password inputted by the user

MessageDigest md = MessageDigest.getInstance(“MD5”);

md.update(original.getBytes());

byte[] digest = md.digest();

StringBuffer sb = new StringBuffer();

for (byte b : digest) {

sb.append(String.format(“%02x”, b &amp; 0xff));

}

//End copy/paste

System.out.println(“original:” + original);

System.out.println(“digested:” + sb.toString()); //sb.toString() is what you’ll need to compare password strings

}

}