---
layout: post
title: "Sam Dela Cruz, Launches Site"
date: 2019-09-06
---

Well. Finally got around to putting this old website together. Neat thing about it - powered by [Jekyll](http://jekyllrb.com) and I can use Markdown to author my posts. It actually is a lot easier than I thought it was going to be.

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

```python
import logging
import re

from django.conf import settings

from orchestrator.exceptions import AcquireDockerError
from orchestrator.exceptions import NimbusDockerError
from orchestrator.models import Docker
from orchestrator.utils.common import RemoteExecute

LOG = logging.getLogger(__name__)


def acquire_docker_machine(job_id):
    """
    Acquire docker machine and increment serving.

    Args:
        job_id (int): job id

    Returns:
        Docker orchestrator model object

    Raises:
        AcquireDockerError: when no docker machine available
    """
    docker = Docker.objects.filter(active=True).order_by('serving').first()
    if docker:
        docker.serving += 1
        docker.save(update_fields=['serving'])
        LOG.info(
            "Acquired docker %s for job %s" % (docker.name, job_id))
        return docker
    else:
        error_msg = "Acquire docker failed for job %s. " % (job_id) + \
            "No docker machine available."
        LOG.error(error_msg)
        raise AcquireDockerError(error_msg)
```
