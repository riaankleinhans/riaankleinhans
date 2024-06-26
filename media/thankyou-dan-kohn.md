**[BLOG](https://ii.nz/post/) / [COMMUNITY POST](https://ii.nz/post/cncf-dan/)**

# Thank you Dan Kohn

_By Riaan Kleinhans_

_19th March 2021_

_"He believed in ii, and in all of us."_

This is a story about relationships, and how they are the currency that moves
this world forward. It is a story about ii's relationship with Dan Kohn, and how
his visionary leadership and friendship changed our world, and the open source
community.

## Ships, Servers, and Friends

In 2015, Hippie Hacker consulted for [Chef.io](https://www.chef.io/), with one
of his assignments involving the [Maritime Telecommunications
Network](https://en.wikipedia.org/wiki/Maritime_Telecommunications_Network)
(MTN). Through this assignment, Hippie met Aaron Crickenburger, who at the time
worked for MTN Chief innovation officer Bob Wise.

Aaron and Hippie did amazing things together, deploying hands-off,
over-the-internet, network booting of servers that were then mananged by Chef
software. They spent several weeks together making this happen and through this
developed a friendship that, in the rippling effect of relationships, would
influence the direction of Kubernetes today.


During the MTN project, Bob shipped servers to Hippie's home in Portland,
Oregon, to help with the network-booting work. When Hippie later moved to
Aotearoa New Zealand, he was unable to bring the servers with them. Hippie then
asked Bob if he had any money available to help relocate the servers to Aotearoa
New Zealand. Bob introduced Hippie to someone who could help. This person was
[Dan Kohn](https://en.wikipedia.org/wiki/Dan_Kohn). Bob introduced the two of
them, telling Dan about Hippie's work and values. A relationship was formed, the
servers were relocated, and are still used as part of the infrastructure for
Hippie's vision.

## Balena and Cross-Cloud

Now in Aotearoa New Zealand, Hippie began doing work for [Balena](https://www.balena.io/)
with [Denver Williams](https://github.com/denverwilliams). This technology
enabled the "image pull and networking boot" in new, exciting ways. Inspired,
Hippie set to use this technology with Kubernetes, by pulling down the images
and installing [GitLab](https://about.gitlab.com) on top of it. He showed a demo
of this to Dan who, impressed by this innovative approach to using Kubernetes,
asked Hippie if he'd like to join the CNCF to help demonstrate what the
orginzation is capable of. Hippie jumped in, helping to create a [Demo of CNCF
technologies](https://github.com/cncf/demo/).

While the demo did not get much traction, it was foundational in exploring
ideas which evolved into Hippie's next project with CNCF. Dan had a vision to
get all cloud providers actively engaged in the cloud-native experience. This
vision manifested as [Cross-Cloud](https://github.com/crosscloudci/cross-cloud),
a way to concretely show the work of CNCF through a web
frontend([cncf.ci](https://cncf.ci/)) that showed all the projects available on
participating cloud providers. [Taylor Carpenter](https://github.com/taylor), a
long time friend, continued the project with the [vulk.coop](https://vulk.coop)
team and Hippie moved on to tackle new challenges with Dan.

## The start of Conformance

In 2017 Hippie attended his first CloudNativeCon + KubeCon Europe in Berlin,
Germany. It was here that Dan introduced the Kubernetes conformance standard,
and the Kubernetes Certified Service Provider program.

A year later, in February 2018 [Kenichi Omichi](https://github.com/oomichi) dug
into the Kubernetes logs and found that Kubernetes had 481 API endpoints, only 53
of them were covered by tests. Dan knew that for the [Certified Kubernetes
brand](https://github.com/cncf/k8s-conformance/pulls#certified-kubernetes) to
have meaning, they needed to invest to make sure test coverage was much higher.
The problem was not just a lack of tests, but a lack of visibility--it required
heavy, manual data mining just to calculate coverage in the first place.

To find a solution to this problem, Hippie paired with [Rohan
Fletcher](https://github.com/rohfle). During a discussion with Hippie and Rohan,
Dan showed them a disk usage graph for OSX and proposed they use a similar graph
to visualize Conformance coverage of the Kubernetes API.

![dans vision screenshot](images/disk_graph.png)


## APISnoop

Rohan started on the project to create what would be
[APISnoop](https://apisnoop.cncf.io/): a visual insight into Kubernetes test
coverage. This project was well-received by the community when it was introduced
at Kubecon Europe 2018.

That same year, [Zach Mandeville](https://github.com/zachmandeville) joined the
team and took over development of APISnoop. At that point there was no real
automation for generating Snoop's data. Much was still done by manually looking
for tests in audit event logs. Zach did a lot of the writing, rewriting, and
architectural changes to APISnoop, along with driving updates of underlying
Kubernetes logging so that clear coverage information could be distinguished
from noise.

While APISnoop worked to show gaps in Conformance coverage, a separate effort
was started to fill those gaps with tests. Unfortunately, this effort was slow
going. After about a year, APISnoop showed very little movement on the graph, as
the test writing efforts yielded very little results. Within character, Dan
started to look for other ways to get an increase in coverage happening at a
rate that satisfied his vision.

Since Hippie and his team had been looking at the Kubernetes API and all its
underlying parts for almost a year, it was a logical fit for them to step up to
the test-writing efforts, and work to increase the test writing velocity.

## Test-Writing

The writing of tests was a learning experience for everyone in ii, as well as
the contributors in the Kubernetes community. Initially, the process was to
quietly work on tests, ensuring they fit all known requirements and then, once
they seemed ready, to share it with the community through a PR. These PR's
invariably sparked feedback and needed revisions, and could lead to discussions
on whether the particular test meaningfully changed the coverage at all. The
process for writing, rewriting, and collaborating on tests was slower than
desired.

Hippie and the ii team-- notably Devan Carpenter, [Caleb
Woodbine](https://github.com/bobymcbobs), and [Stephen
Heywood](https://github.com/heyste)-- came up with the mock test concept, using
org-mode in their own flavor of [Emacs (Humacs)](http://humacs.org/)
deployed on a Kubernetes cluster. Zach decoupled the APISNoop database from the
app , so that it could be deployed to the cluster and used as part of a
test-writing environment. This allowed for tighter feedback loops, with test
writers able to immediately see whether their mock test hit the endpoints they
expected. These mock tests, along with their projected results as calculated by
APISnoop, were then presented at the SIG Architecture Conformance sub-project
meetings for initial approval, before creating the actual tests and pull
requests.

The Kubernetes project is a complex organism, with a vast community and diverse
[Special Interest Groups](https://github.com/kubernetes/community) (SIG’s).
Conformance works across all these organizational levels, and reaching consensus
on it is an equally complex task. The collaborative test-writing method of
Hippie’s team helped increase the velocity and transparency of test writing.


## Iterations and Automations

Dan was always pushing the bar higher, continually expecting better and clearer
results out of APISnoop so it would be a well-used tool throughout the
Kubernetes community. This inspired Zach and ii to continually improve its
functionality, changing APISnoop from a static page showing only the current
status of conformance, to a multi-faceted tool with multiple ways to view not
just the current data, but the historical progress of Conformance. Hippie
developed a unique Kind+APISnoop combination that allowed anyone to access the
querying power of APISnoop locally.

![Test Cover 1.15](images/1_15Cover.png)
<figcaption>
 Test Cover 1.15
</figcaption>

![Test Cover 1.21](images/1_21cover.png)
<figcaption>
Test Cover 1.21
</figcaption>

![Conformance progress chart](images/Conformance-progress.png)

<figcaption>
Conformance Progress graph
</figcaption>

The increased conformance coverage was great news, and added the expected value
to the Certified Kubernetes brand. At the same time, it was making life
increasingly difficult for [Taylor Waggoner](https://github.com/taylorwaggoner)
at the CNCF to manage the Conformance Certification process. All pull requests
for certification had to be manually verified to ensure it contained all tests,
but the list of conformance tests kept growing with each release.

Dan approached Hippie and requested the process to be automated, and in 2020 the
CNCF CI Bot was created by [Berno Kleinhans ](https://github.com/bernokl)and
[Rob Kielty](https://github.com/RobertKielty). This allowed for the automatic
checking and labeling of conformance pull requests, speeding up the process and
reducing the human effort needed.

## Thank you

The Kubernetes Conformance journey up to this day is an eventful one, built
around relationships and community cooperation, with many different contributors
playing their part to help move this forward. All of this was made possible by
the extraordinary vision and leadership of a friend dear to everyone in the
Kubernetes community: Dan Kohn.

![Dan Kohn](images/dan_kohn.jpg)

<figcaption>
Dan Kohn
</figcaption>