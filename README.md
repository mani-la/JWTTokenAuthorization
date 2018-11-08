# JWTTokenAuthorization
Easy way to implement JWT Token Authorization for .NET 

This JWT Authorization is the easiest way to implement JWT Token Authentication in your .Net Web Api or MVC App.

Add JWTAuthorization.dll file into your project reference like below,

 * Right click project and select "**Add Reference**" option.
 * Browse this dll and add it to the project.
Create configuration keys and set values for the JWT Token,

<appSettings>
<add key="JWTissuer" value="self"/>
<add key="JWTaudience" value="www.website.com"/>
</appSettings>

Implement the below code inside login method to generate the JWT Token,
TokenAuthorize authentication = new TokenAuthorize(DateTime.Now,DateTime.Now.AddDate(1));
string JWT_Token = authentication.GenerateTokenForUser(user.u_name, user.u_id);

 * TokenAuthorize has 2 parameters,
    1. First parameter is a date that is valid from the token
    2. Second parameter is a data that is expired on for the token
Implement [JWTAuthorize] on the top of the controller or action method which needs to be authenticate by the token like below,
For Action method,

[JWTAuthorize]
[HttpGet]
[ActionName("isExists")]
public IHttpActionResult IsUserExists(string uname=null, string email=null)

For Controller,

[JWTAuthorize]
public class UserController : ApiController

That's all implementation done from the server side.
