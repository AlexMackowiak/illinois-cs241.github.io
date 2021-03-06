{% if page.submissions %}
## Submission Instructions

Please read details on [Academic Integrity]({{ site.url }}/#academic-integrity) fully. These are shared by all assignments in CS 241.

We will be using Subversion as our hand-in system this semester. Our grading system will checkout your most recent (pre-deadline) commit for grading. Therefore, to hand in your code, all you have to do is commit it to your Subversion repository.

{% assign filename = page.url | replace_first: '/', '' | replace: '/', '-'  | replace: '.html', '.md' %}
{% assign submit_dir = page.svn_dir | default: filename %}
To check out the provided code for <code class="highlighter-rouge">{{ filename }}</code> from the class repository, go to your cs241 directory (the one you checked out for "know your tools") and run:

```
svn up
```

If you run `ls` you will now see a `{{ submit_dir }}` folder, where you can find this assignment! To commit your changes (send them to us), type:

```
svn ci -m "{{ filename }} submission"
```

Your repository directory can be viewed from a web browser from the following URL: [https://subversion.ews.illinois.edu/svn/{{ site.semester }}-{{ site.subject_code }}{{ site.course_number }}/NETID/{{ submit_dir }}](https://subversion.ews.illinois.edu/svn/{{ site.semester }}-{{ site.subject_code }}{{ site.course_number }}/NETID/{{ submit_dir }}), where NETID is your University NetID. It is important to check that the files you expect to be graded are present and up to date in your SVN copy.

## Assignment Feedback

We strive to provide the best assignments that we can for this course, and we would like your feedback on them!

This is the form we will use to evaluate our assignments. We appreciate the time you take to give us your honest feedback and we promise to keep improving the course to make your experience in CS 241 the best it can be.

[https://goo.gl/forms/hREf0ojFWumYfQF12](https://goo.gl/forms/hREf0ojFWumYfQF12)
{% endif %}
