---
layout: post
title:  "linux commands execution in java"
date:   2015-12-15 12:35:58 +0200
categories: development
---
if you want to execute linux commands in java with multiple parameters and pipes (|)
you need to:

{% highlight java %}
 private static String executeCommand(String command) {
        String[] cmd = {
                "/bin/sh",
                "-c",
                command
        };
        StringBuilder output = new StringBuilder();
        Process p;
        try {
            p = Runtime.getRuntime().exec(cmd);
            p.waitFor();
            BufferedReader reader =
                    new BufferedReader(new InputStreamReader(p.getInputStream()));
            String line;
            while ((line = reader.readLine())!= null) {
                output.append(line).append("\n");
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
        return output.toString();
    }
   {% endhighlight %}

 now you can pass commands wiht pipes as a regular string