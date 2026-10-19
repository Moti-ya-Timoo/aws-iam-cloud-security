<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](https://nextwork.ai/projects/51a5fd24-7458-58a6-8653-9b90119a0e4a)




---  

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1c864649)

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM to control access and permission settings in my AWS account. I'm doing this project to learn about cloud security from the absolute foundations - every company thinks about access permissions and there are even entire jobs called IAM Engineers focused on the skills I'm about to build today.

### Tools and concepts

Services I used were Amazon EC2 and AWS IAM.
Key concepts I learnt include IAM users, policies, user groups, and account aliases. I also learned how to use policy simulator and how JSON policies work.
In addition, how to launch an instance. Basically, how to tag an instance, how to log in as another user. 

### Project reflection

This project took me approximately two hours today including demo time.
The most challenging part was understanding the IAM Policy since it was written in JSON and it  contained multiple statements.
It was most rewarding for me to see permission denied when my intern tried to delete my production instance. My IAM access management set-up was working.

## Tags

### What I did in this step

In this step, I will launch two EC2 instances because I need to boost NextWork's computing power - I'm expecting more users and traffic into our website over the summer break!

### Understanding tags

Tags are organizational tools that lets us label our resources. They are helpful for grouping resources, cost allocation, and applying policies for all resources with the same tag.


### My tag configuration

The tag I’ve used on my EC2 instances is called environment. The value I’ve assigned for my instances are production and development.

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_2e0e5a5d)

## IAM Policies

### What I did in this step

In this step, I will use IAM policies to control the access level as a new Nextwork Intern, because they should have acess to the development environment i.e. the development instance, but not the production environment.

### Understanding IAM policies

IAM Policies are like rules that determine who can do what in our AWS account. For this project, I've set up a policy using JSON. I'm using policies today to control who has access to our production environment instance.

### The policy I set up

For this project, I’ve set up a policy using JSON.

### Policy effect

I’ve created a policy that allows the policy holder in my case the Intern to have permission to do anything they want to any instance tagged with development. They can also see information related for any instance, but they're denied access to deleting or creating tags for any instance as well.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means whether or not the policy is alowing or denying action which is the effect. What the policy holder can or cannot do. That's the action, and the specific AWS resources that the policy relates to i.e. resource.

## My JSON Policy

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1c864649)

## Account Alias

### What I did in this step

In this step, I will set up an account alias which is like a nickname for my AWS consoles login portal or a nickname for a AWS account console login. This is because an account alias makes it simpler for my users to log in.

### Understanding account aliases

An account alias is simply a nickname for my AWS account instad of a long account ID. I can now reference my account alias instad.

### Setting up my account alias

Creating an account alias took me about 1 minute - its a simple configuration in the IAM dashboard. 
Now, my new AWS console sign-in URL uses the alias instead of my acoount ID.

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0eb4439b)

## IAM Users and User Groups

### What I did in this step

In this step, I will set up two resources IAM users and IAM user groups. This is because IAM users are like logins for people that want access to my AWS account, while user groups are like folders to manage users that have the same level of access. 

### Understanding user groups

IAM user groups are like folders that collect IAM users so that you can apply permission settings at the group level.

### Attaching policies to user groups

I attached the policy I created to this user group, which means any user created inside this group will automatically get the permissions attached to my NextWorkDevEnvironmentPolicy IAM policy.

### Understanding IAM users

IAM users are people or entities that have access or can login to your AWS account.

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email sign-in instructions to the user,
while the second way is to download the csv file with the sign-in details inside.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that my user is already denied access to items or panels on the main AWS console dashboard. 
This was because we only set-up permissions to EC2 to our development EC2 instance. So my intern wouldn't have access to anything else and even see anything else.

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_6f2ab446)

## Testing IAM Policies

### What I did in this step

In this step, I will login to my own AWS account as the intern and test access to the production and development instances because I want to make sure my intern doesn't have the ability to do anything that can affect my production instance or my production environment. 

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the development and the production instances.

### Stopping the production instance

When I tried to stop the production instance I was met with an error.
This was because our production instance is tagged with the production label which is outside of the scope of our permission policy.
Interns are only allowed to do things to the development instance.

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, I successfully saw the instance state changed to stopping and then stopped.
This was because our persission policy allows the intern i.e. users in the nextworkdev group to stop instances.

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_1811801c)

## IAM Policy Simulator

To extend my project, I'm going to test my permission policies in a safer and more controlled way. A tool called the IAM policy simulator 
I'm doing this because having to stop instances and log into AWS accounts as other users is a bit disruptive.
Let#s find a more efficient way.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that lets us simulate actions and test permission settings by defining a specific user, a specific group, a specific role, and the action we want to test for.
It's useful for saving time when testing permission setings. No more logging into another user or actually stopping resources.

### How I used the simulator

I set up a simulation for whether our development or dev user group has permission to stop instances or delete tags.
The results were denied for both. 
I had to adjust the scope of the ec2 instances to ones that are tagged with development. Once I applied that tag, permission was allowed. 

![Image](https://nextwork.ai/serene_orange_proud_wolf/uploads/51a5fd24-7458-58a6-8653-9b90119a0e4a_069d8a621)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/51a5fd24-7458-58a6-8653-9b90119a0e4a)*
