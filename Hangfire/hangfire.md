<!--
 * @Author: your name
 * @Date: 2021-04-23 14:12:56
 * @LastEditTime: 2021-04-23 14:13:10
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Hangfire\hangfire.md
-->
https://qinyuanpei.github.io/posts/1071063696/


//Fire-and-forget jobs
var jobId = BackgroundJob.Enqueue(
    () => Console.WriteLine("Fire-and-forget!"));

//Delayed jobs
var jobId = BackgroundJob.Schedule(
    () => Console.WriteLine("Delayed!"),
    TimeSpan.FromDays(7));

//Recurring jobs
RecurringJob.AddOrUpdate(
    () => Console.WriteLine("Recurring!"),
    Cron.Daily);

//Continuations
BackgroundJob.ContinueWith(
    jobId,
    () => Console.WriteLine("Continuation!"));