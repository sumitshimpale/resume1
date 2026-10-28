# DevOps Interview Question Bank — 3 to 5 Years Experience
**Tailored to: Sumit Shimpale — DevOps Engineer (Worldpay / TCS, Pune)**

Legend: ⭐ = most frequently asked / highest-probability in a real interview.
*Italic text = what the interviewer is really testing.*

---

## How to Use This Document

1. **Start with the "Top 30 Must-Ask"** (Part A) — these come up in almost every DevOps interview.
2. **Every tool on your resume has its own section.** Questions are ordered from most-asked to least-asked.
3. **Your resume numbers are your assets.** Every bullet you wrote (35%, 30%, 25%, 400+ servers, 200+ instances, 99.9% uptime, 45 minutes, 15+ microservices) is a claim you must be able to defend. Part L has the deep-dive questions built from your actual experience.
4. **Be honest about depth.** You have 3–5 years, not 10. "I used this in production, here's exactly what I did" beats a textbook recital of something you only read about. If you know a tool only at the surface, say so and describe what you *would* do — interviewers reward that in the 3–5 band.

---

# PART A — TOP 30 MUST-ASK QUESTIONS

These are the highest-frequency questions across DevOps interviews. If you master only these, you cover the most ground.

### Cloud & Containers
1. ⭐ **Explain the difference between a container and a virtual machine.** Where does the container boundary sit, and what does that change for isolation, startup time, and resource usage?
2. ⭐ **Walk me through what happens from `kubectl apply` to a running pod.** (Admission → scheduler → kubelet → CNI → runtime → container start → probes.)
3. ⭐ **What is the difference between a Deployment, StatefulSet, and DaemonSet?** Give a real workload for each.
4. ⭐ **What are liveness, readiness, and startup probes, and what happens if you configure them wrong?**
5. ⭐ **How do you expose a Kubernetes service outside the cluster?** Compare ClusterIP, NodePort, LoadBalancer, and Ingress — and when you'd use each.
6. ⭐ **Explain VPC, subnets, route tables, NAT Gateway, and Internet Gateway.** Draw the path of an outbound request from a pod in a private subnet.
7. ⭐ **What is the difference between a security group and a NACL?** How do they differ in statefulness and evaluation order?
8. ⭐ **Explain IAM roles, policies, and least privilege.** Why is it risky to attach a broad policy to an EC2 instance instead of an instance profile?
9. ⭐ **Walk me through the components of an EKS cluster.** Who manages the control plane, and who manages the worker nodes?
10. ⭐ **ALB vs NLB — when do you use which?** What is the difference in target type and health check behavior?

### CI/CD & IaC
11. ⭐ **What is the difference between CI and CD?** How do "continuous delivery" and "continuous deployment" differ?
12. ⭐ **Describe the stages of a Jenkins pipeline you would build for a Java microservice.** (Checkout → build → test → SCA/SAST → container build → push → deploy → verify → rollback.)
13. ⭐ **What is a GitHub Actions workflow?** Explain `jobs`, `steps`, `runs-on`, and how you pass artifacts between jobs.
14. ⭐ **What is Terraform state and why does it matter?** What happens if two engineers run `apply` at the same time?
15. ⭐ **What is the difference between `plan` and `apply`?** How do you review a plan before it reaches production?
16. ⭐ **How do you keep secrets out of a CI pipeline?** (Secrets manager, OIDC federation, masked secrets — and never in git.)

### Linux, Scripting & Troubleshooting
17. ⭐ **How do you find a process that is consuming CPU/memory?** Explain `top`, `ps`, `free`, `df`, `du`, `iostat`, and how you'd read them.
18. ⭐ **What is the difference between a process and a thread?** How do you troubleshoot a Java application that is hanging?
19. ⭐ **Explain the JVM memory model.** What are the young and old generations, and what causes a Full GC pause?
20. ⭐ **What steps do you take when a production service goes down?** Walk me through your incident-response runbook.
21. ⭐ **What is a heap dump vs a thread dump?** When would you take each, and how do you analyze them?

### Monitoring & Messaging
22. ⭐ **What is Prometheus, and how does the pull model work?** Why is it a good fit for Kubernetes?
23. ⭐ **Write me a PromQL query** to compute the 99th-percentile request latency. Explain `rate()` vs `irate()`.
24. ⭐ **What is the difference between a Deployment, ReplicaSet, and a StatefulSet for a Kafka or DB workload?** (covered above — combine)
25. ⭐ **What is Kafka partitioning, and how does it affect ordering and throughput?**
26. ⭐ **Explain the Kafka consumer group and rebalancing.** What is consumer lag and how do you fix it?
27. ⭐ **What does `acks=all` mean in Kafka, and what is the trade-off?** (same as #25/#26 — see Part J)
28. ⭐ **How do you design an alerting strategy?** What makes an alert good vs noisy?

### Middleware & Security
29. ⭐ **What is a JVM deadlock?** How do you identify it from a thread dump and what are the typical causes?
30. ⭐ **What is the SSL/TLS handshake?** Explain certificate chains, the CA's role, and what happens if a certificate expires.

---

# PART B — DEVOPS FUNDAMENTALS & PROCESS

1. ⭐ **What does DevOps mean to you, and how is it different from just "using the cloud"?**
   *Testing: culture/practice framing, not tool-list framing.*
2. ⭐ **How do you measure the success of a CI/CD pipeline?** Which DORA metrics do you track (deployment frequency, lead time for changes, change failure rate, time to restore)?
3. ⭐ **Explain the common deployment strategies** — rolling, blue/green, canary, A/B, recreate. When would you pick each?
4. ⭐ **What is an SLO, SLI, and error budget?** How does an error budget change engineering decisions?
5. ⭐ **What is the difference between SLAs, SLOs, and SLIs?**
6. ⭐ **How do you design a rollback strategy?** What is the difference between rolling back a release and rolling forward a fix?
7. ⭐ **What is a GitOps workflow?** How does it differ from a push-based CI/CD pipeline?
8. ⭐ **How do you manage configuration and secrets across environments?** (config files, secret managers, environment parity.)
9. ⭐ **What is the difference between a monolithic application and microservices from a DevOps perspective?** What does each do to your CI/CD and monitoring complexity?
10. ⭐ **How do you handle a failed deployment?** Walk me through your decision tree.
11. ⭐ **What is an artifact repository and why do you need one?** (ECR, Nexus, Artifactory.)
12. ⭐ **What is infrastructure as code, and why should you never click "Launch Instance" in the console?**
13. ⭐ **What is a change advisory board (CAB) and how do you handle production changes?** (Relevant to your TCS/banking background.)
14. ⭐ **Explain incident severity levels (P1–P4) and what response each requires.**
15. **What is a RACI matrix, and how do you use it in a change?**
16. **How do you handle a change on Black Friday / a peak-traffic freeze?**
17. **What is drift detection and why does it matter?**
18. **How do you manage multi-region deployments and what failure modes do you design for?**
19. **What is the difference between blue/green and canary?** (Depth follow-up.)
20. **How do you version your infrastructure and application together?** (GitOps vs "one repo, two folders.")

---

# PART C — LINUX & OPERATING SYSTEM

1. ⭐ **How do you check disk usage and find the top 10 directories consuming space?** (`du -h --max-depth=1 | sort -h`, `df -h`, `ncdu`)
2. ⭐ **Explain file permissions and ownership.** What does `chmod 750` mean? What is the setuid bit?
3. ⭐ **What is the difference between `kill`, `kill -9`, `kill -15`, and `pkill`?** When is each appropriate?
4. ⭐ **Explain process states and how to use `ps aux`, `top`, `htop`, and `strace` to debug a hung process.**
5. ⭐ **How do you find which process is listening on a port and how do you free it?** (`ss -tulpn`, `lsof -i :8080`, `fuser`)
6. ⭐ **What is the difference between a process and a thread from an ops perspective?** (Memory isolation, GIL in Python, JVM threads.)
7. ⭐ **Explain systemd.** How do you write a unit file, enable a service at boot, and read its logs?
8. ⭐ **How do you find and kill a runaway process consuming 100% CPU?** How do you identify the parent?
9. ⭐ **Explain the Linux boot process at a high level** and where you'd insert troubleshooting.
10. ⭐ **How do you analyze a slow disk?** What do `iostat`, `iostat -x 1`, `vmstat`, and `sar` tell you?
11. ⭐ **What is `swap` and when does swapping kill performance?**
12. **How do you find which file a process has open?** (`lsof`, `/proc/<pid>/fd`, `fuser`)
13. **Explain the difference between `cron`, `systemd timers`, and `at`.** What's the crontab syntax?
14. **How do you configure passwordless SSH between hosts?** What are the risks?
15. **How do you troubleshoot a host that is out of disk space and can't log in?**
16. **What is `/etc/fstab` and how do you mount a filesystem at boot?**
17. **Explain how DNS resolution works and how you'd debug a name resolution failure.** (`dig`, `nslookup`, `host`, `/etc/resolv.conf`)
18. **What is the difference between `curl` and `wget` for health checks?** How would you check a URL returns 200?
19. **How do you monitor memory on Linux and identify a memory leak?** (`free -m`, `vmstat`, `smaps`, cgroups)
20. **Explain `grep`, `awk`, `sed`, `xargs`, and `cut`.** Which would you use to extract column 3 of a log?
21. **What is a symlink vs a hard link?**
22. **How do you rotate logs?** (`logrotate`, `copytruncate` vs `create` — why does it matter for processes holding file handles?)
23. **What are file descriptors and the ulimit?** How do you raise the open-file limit for a service?
24. **How would you find the biggest memory consumers among Java processes?**
25. **Explain `uptime` and load average** — why can load average exceed CPU count?

---

# PART D — SHELL / BASH SCRIPTING

*Your resume claims shell automation across 400+ production servers — expect deep questions here.*

1. ⭐ **Write a script that checks whether a service is running and restarts it if not.** How would you make it safe to run repeatedly (idempotency)?
2. ⭐ **What is `set -e`, `set -u`, `set -o pipefail`, and `set -x`?** Why would you use them together?
3. ⭐ **Explain exit codes.** How do you propagate a failure from a script that runs several commands?
4. ⭐ **What is the difference between `"$var"` and `$var`?** Why does quoting matter?
5. ⭐ **Explain the difference between a pipe and a redirect.** What is `2>&1` doing exactly?
6. ⭐ **How do you pass arguments to a script, and how do you read them?** (`$1`, `$@`, `$*`, `shift`, `getopts`)
7. ⭐ **Write a health-check script** that validates an HTTP endpoint, checks a response code and body, and exits non-zero on failure.
8. ⭐ **How do you capture the output of a command, including stderr?** (`$(...)`, backticks, `2>&1`)
9. ⭐ **How do you run a command in the background and check if it's still running?** (`&`, `wait`, `$!`, `nohup`, `disown`)
10. ⭐ **Explain process substitution and its use over temporary files.**
11. **What is a here-document and here-string?** When do you use them?
12. **How do you work with associative arrays in Bash?** (Used to build lookup maps — a common real-world pattern for multi-server automation.)
13. **How do you parallelize work across 400 hosts?** (`xargs -P`, `GNU parallel`, background jobs + `wait`) What are the risks?
14. **How do you write a cron job that runs a script and emails you only on failure?** (exit code → conditional execution)
15. **What is a trap and when do you use one?** (cleanup of temp files, locking)
16. **How do you handle errors in a long script?** (error trapping, logging, `trap '...' ERR`)
17. **How do you source another script safely vs execute it?**
18. **Write a function that returns the exit status of a pipeline.**
19. **How do you parse JSON in a shell script?** (`jq`) Show an example extracting a field from a nested structure.
20. **How do you parse XML/HTML output?** (`xmllint`, `grep -oP`, `sed`)
21. **What is the difference between `curl -f` and `curl -s`?** How do you capture both headers and body?
22. **How do you make a script safe against concurrent execution?** (flock, lock files)
23. **Explain `rsync` and its most useful flags.** (`-avz`, `--delete`, `--exclude`, `--dry-run`) Why is `--delete` risky?
24. **How do you copy an SSH key to many hosts?** (`ssh-copy-id`, ssh config, Ansible)
25. **How do you store and rotate a password used by a script?** (Never plaintext — `aws secretsmanager`, `vault`, `pass`)
26. **What is the difference between `>` and `>>`?** What about `2>`?
27. **How do you find text in a large set of log files efficiently?** (`grep -r`, `zgrep`, `awk`, `find | xargs`)
28. **Explain `sed 's/a/b/g'` vs `sed -i` vs `awk '{gsub(...)}'`.**
29. **How do you handle a command that may hang?** (`timeout`, `curl --max-time`)
30. **What is the difference between `source`, `.`, and `bash script.sh`?** (environment variable scope)

---

# PART E — PYTHON

1. ⭐ **Write a Python script that calls a REST API and retries with exponential backoff.** How do you decide the retry count and the ceiling?
2. ⭐ **How do you pass arguments to a Python script?** (`argparse`) Why is it better than `sys.argv` directly?
3. ⭐ **How do you read and write files safely?** (context managers, `with`, `pathlib`)
4. ⭐ **Explain the difference between a list, tuple, set, and dictionary.** When would you use each?
5. ⭐ **How do you handle exceptions?** Difference between `except Exception`, bare `except`, and `except SpecificError`?
6. ⭐ **What is a virtual environment?** Why do you need it? (`venv`, `requirements.txt`, `poetry`)
7. **Explain list/dict comprehensions.** When is a comprehension worse than a loop?
8. **What are decorators and generators?** Show a simple example of each.
9. **How do you call an external command from Python?** (`subprocess.run` with `check=True`, `capture_output=True`) Why is `shell=True` risky?
10. **How do you work with JSON and YAML in Python?** Which module for each, and what's the YAML security caveat (`yaml.load` vs `yaml.safe_load`)?
11. **What are the different ways to write a unit test in Python?** (`pytest`) How do you mock an API call?
12. **How would you use `boto3` to fetch an AWS secret?** How do you avoid hardcoding credentials?
13. **What is the difference between a module and a package?** What does `__init__.py` do?
14. **How do you connect to a database from Python?** (connection pooling, parameterized queries — SQL injection)
15. **Explain `__name__ == "__main__"`.**
16. **What is the GIL, and does it matter for your scripts?**
17. **How would you parallelize independent work in Python?** (`multiprocessing` vs `threading` vs `asyncio` vs `concurrent.futures`)
18. **How do you write a small HTTP client without a framework?** (`requests` vs `urllib`)
19. **How do you schedule a Python job?** (`cron`, systemd timer, Airflow, EventBridge Scheduler)
20. **How do you profile a slow Python script?** (`cProfile`, `line_profiler`, `timeit`)

---

# PART F — GIT

1. ⭐ **What is the difference between `git merge` and `git rebase`?** When is a rebase dangerous?
2. ⭐ **Explain `git reset` vs `git revert` vs `git checkout`.** When does each apply?
3. ⭐ **What is a detached HEAD, and how do you get out of it?**
4. ⭐ **Explain `git cherry-pick`.** What workflow is it for?
5. ⭐ **What is `git stash`?** What are the common mistakes people make with it?
6. ⭐ **Describe a branching strategy you've used** (GitFlow, trunk-based, GitHub Flow). When does GitFlow break down?
7. **How do you resolve a merge conflict?** Walk through the steps in a real example.
8. **What is `git bisect` and how do you use it to find a bad commit?**
9. **What are git hooks?** How would you enforce commit message format or run a linter on pre-commit?
10. **What is the reflog and how did it save you?**
11. **What is `git commit --amend` used for? When is it dangerous?**
12. **What is the difference between `git fetch`, `git pull`, and `git clone`?** What does `git pull --rebase` do?
13. **Explain `git log` options you'd use to find who changed a line:** `git blame`, `git log -p`, `git log --follow`.
14. **What is a shallow clone and when do you need it?** (`--depth 1`)
15. **How do you sign commits and why?** (`GPG`, SSH signing, commit signing for supply-chain integrity)
16. **How do you undo a commit that was already pushed?** (revert vs force-push — and why force-push to a shared branch is dangerous)
17. **What is `git worktree` and when do you use it?**
18. **How do you handle large files in git?** (Git LFS, `.gitignore` patterns, `git rm --cached`)
19. **How would you revert an entire merge commit?** (`git revert -m 1 <sha>`)
20. **Explain `.gitignore` vs `.git/info/exclude` vs a global gitignore.**
21. **How do you squash many commits into one before opening a PR?**
22. **What is `git replace` and `git filter-repo`?** When have you needed to rewrite history?

---

# PART G — MAVEN

*Your resume says CI/CD for 15+ Java microservices — Maven questions will show up.*

1. ⭐ **What is the Maven build lifecycle?** List the default lifecycle phases for `jar` packaging and where `test` fits.
2. ⭐ **What is the difference between a plugin *goal* and a lifecycle *phase*?** Give an example of each.
3. ⭐ **How do you skip tests in Maven, and why is that dangerous in CI?**
4. ⭐ **What is a `pom.xml`?** Explain `<groupId>`, `<artifactId>`, `<version>`, `<packaging>`, and `<parent>`.
5. ⭐ **What is the Maven dependency tree?** How do you find and resolve a dependency conflict? (`mvn dependency:tree`, `dependencyManagement`, `exclusions`)
6. ⭐ **What are the dependency scopes** — `compile`, `provided`, `runtime`, `test` — and what does each mean?
7. **What is the difference between `SNAPSHOT` and a release version?** How does the repository treat them differently?
8. **What is a multi-module Maven project?** How does the reactor build order work and what is `-pl` and `-am` for?
9. **Explain `<properties>`, `<dependencyManagement>`, and `<profiles>`.** When would you use a profile?
10. **What is the difference between `mvn install` and `mvn deploy`?** Where does each put the artifact?
11. **What does `mvn -o` (offline) do and when is it useful?**
12. **What is `mvn clean install` and does `clean` matter for reproducibility?**
13. **How do you configure Maven to use a corporate repository and a mirror?** (settings.xml, `mirrorOf`)
14. **What are Maven Wrapper (`mvnw`) and `.mvn/wrapper`?** Why does CI use them?
15. **What is the difference between `mvn package` and `mvn verify`?**
16. **How do you run only integration tests in a Maven build?** (failsafe plugin, `*IT.java`)
17. **How do you publish a Docker image from a Maven build?** (Jib, docker-maven-plugin, or build outside Maven — which do you prefer and why?)
18. **What is `maven-enforcer-plugin` and why is it used in enterprise builds?**
19. **How do you control Java version across a team?** (`maven.compiler.release`, `toolchains`) Why does `release` beat `source`/`target`?
20. **How do you generate a build with an SBOM or signed artifacts?** (CycloneDX, `sign-maven-plugin`) — ties into supply-chain security.
21. **What is a `settings.xml` vs a `pom.xml`?** Which one holds the private repo password, and where should that secret actually live?
22. **How do you speed up a slow Maven build?** (parallel `-T`, build cache, incremental, dependency caching in CI)

---

# PART H — DOCKER

1. ⭐ **What is the difference between a Docker image and a container?** What is a layer?
2. ⭐ **Explain `ENTRYPOINT` vs `CMD`.** What happens if both are set, and why is shell-form `CMD` risky?
3. ⭐ **Write a production-grade Dockerfile for a Java Spring Boot app.** Why multi-stage build? Why run as non-root?
4. ⭐ **What is `docker exec` vs `docker run`?** How do you debug a running container?
5. ⭐ **Explain Docker networking** — bridge, host, none, and overlay. Which one does Compose use by default?
6. ⭐ **How do you limit CPU and memory for a container?** What happens when it exceeds the limit?
7. ⭐ **What is `docker-compose`?** Explain `services`, `networks`, `volumes`, and `depends_on`. Is it for production?
8. ⭐ **How do you reduce image size?** (alpine vs slim vs distroless, multi-stage, `.dockerignore`)
9. **What is the difference between `docker pull` and `docker build`?** Where do images live (layers cache)?
10. **What are Docker volumes vs bind mounts?** When would you use each, and which one is riskier?
11. **Explain container health checks** — `HEALTHCHECK` in the Dockerfile vs a Kubernetes probe.
12. **How do you view and filter container logs?** (`docker logs`, `docker stats`) What are the different logging drivers?
13. **What is `ARG` vs `ENV` in a Dockerfile?** When is each appropriate, and what is the security implication?
14. **How do you scan images for vulnerabilities?** (Trivy, Docker Scout) What do you do with a Critical finding?
15. **What is `docker system prune`?** Why is it dangerous in production?
16. **How do you run a container as a specific non-root user with a read-only filesystem?**
17. **Explain Docker's storage driver** — overlay2 vs aufs — and how the image cache works.
18. **How would you debug a container that exits immediately?** (exit code inspection, `docker logs`, entrypoint override)
19. **What is a multi-stage build, and what goes in the final stage?**
20. **How do you pass a secret into a container build without baking it into the image?** (BuildKit `--secret`, build args vs `RUN --mount=type=secret`)
21. **What is the difference between `docker stop` and `docker kill`?** What timeout does `stop` wait for by default?
22. **How do you tag and push images?** What's the difference between a mutable and immutable tag, and why should production use a digest?
23. **What is an image registry and how do you authenticate to ECR?** (vs a plain `docker login` with a static password)
24. **Explain container PID namespace and how it affects what you see in `ps` inside vs outside.**

---

# PART I — KUBERNETES

*The heaviest section — Kubernetes is the single most-asked tool for a 3–5 year DevOps role.*

## Core Workloads
1. ⭐ **What is a Pod?** Why can't you deploy a container directly to a node without one?
2. ⭐ **What is the difference between a Deployment, ReplicaSet, StatefulSet, and DaemonSet?** When do you need a StatefulSet?
3. ⭐ **What is a Job vs a CronJob?** How do you handle a failed or long-running job?
4. ⭐ **Explain `rolling update` strategy** — `maxSurge`, `maxUnavailable`. How do you achieve zero downtime?
5. **What is a PodDisruptionBudget?** When do you need one?
6. **What is a `ConfigMap` vs a `Secret`?** How should secrets actually be handled in production?
7. **What is a `ServiceAccount`?** Why does Kubernetes create a `default` ServiceAccount per namespace?
8. **What are `labels` and `selectors`?** How do selectors drive `Deployment` → `Pod` matching?

## Services & Ingress
9. ⭐ **Explain the four Service types** — ClusterIP, NodePort, LoadBalancer, ExternalName — with a use case for each.
10. ⭐ **What is an Ingress?** How does it differ from a Service? What ingress controller do you use on EKS?
11. ⭐ **What is `Ingress` path-based routing vs host-based routing?** What happens with path precedence?
12. **What is a headless Service and when do you use it?** (StatefulSet stable DNS)
13. **How does `ExternalName` work and what is it for?**

## Scheduling & Resources
14. ⭐ **How does the scheduler place a pod?** Explain node selectors, node affinity, taints/tolerations, and topology spread constraints.
15. ⭐ **What are resource requests and limits?** What happens if you don't set them? Explain QoS classes (Guaranteed, Burstable, BestEffort).
16. ⭐ **Explain the difference between `requests.cpu`, `limits.cpu`, `requests.memory`, and `limits.memory`.** Why is CPU throttling different from OOM-kill?
17. **What is a Horizontal Pod Autoscaler?** What metric does it use by default, and what does `behavior` do?
18. **What is a Vertical Pod Autoscaler and when is it better than HPA?**
19. **What is the difference between a Pod and a Deployment in terms of self-healing?** Who restarts a crashed pod?
20. **What is a node pool in EKS?** Managed node groups vs self-managed?

## Probes & Troubleshooting
21. ⭐ **Explain liveness, readiness, and startup probes.** Give the exact failure mode for each if misconfigured.
22. ⭐ **A pod is in `CrashLoopBackOff`. Walk me through every command you'd run to diagnose it.**
23. ⭐ **A pod is `Pending`. What are the possible causes?** (insufficient CPU/memory, unschedulable due to taints, PVC pending, image pull)
24. ⭐ **A pod is `ImagePullBackOff` — what do you check?** (image name, tag, registry auth, ECR token expiry)
25. ⭐ **A pod is `OOMKilled`. How do you confirm and fix it?**
26. **A service has no endpoints. What do you check?** (selector mismatch, readiness failing, namespace, headless)
27. **How do you check pod events and previous container logs?** (`describe`, `--previous`)
28. **What is `kubectl debug` / ephemeral containers and how do they help?**
29. **How do you get a shell into a container?** (`kubectl exec -it`, `kubectl cp`, ephemeral debug)
30. **How do you view and export logs?** (`kubectl logs`, `--since`, `--tail`, `-f`, `--all-containers`, sidecar logs)
31. **What is `kubectl top` and what does it require?** (metrics-server / Metrics API)

## RBAC & Security
32. ⭐ **Explain RBAC in Kubernetes.** Difference between Role, ClusterRole, RoleBinding, ClusterRoleBinding, and ServiceAccount.
33. ⭐ **What is the default ClusterRole `cluster-admin` and why should you never bind it broadly?**
34. **What is a Pod Security Admission / Pod Security Standard?** What are the three levels (privileged, baseline, restricted)?
35. **What are NetworkPolicies and how do they work?** (default-deny pattern)
36. **How do you run a workload with a specific service account and cloud permissions?** (IRSA — IAM Roles for Service Accounts)
37. **What is a Kubernetes Secret and why is it insecure by default?** (base64, not encryption) How do you enable encryption at rest?

## Storage & Configuration
38. ⭐ **Explain PV, PVC, StorageClass, and `ReadWriteOnce` vs `ReadWriteMany`.** What does the access mode actually control?
39. **What is `volumeClaimTemplates` and how does it make a StatefulSet stable?**
40. **What is the difference between `emptyDir`, `hostPath`, `configMap`, and `secret` volume types?** When do you use each?
41. **How do you mount a ConfigMap as a volume vs as environment variables?** When would you prefer each?

## Operations & Ecosystem
42. ⭐ **How do you upgrade an EKS cluster?** What's the difference between control plane and managed node group upgrades?
43. **What is Helm?** What are the concepts (chart, release, values, templates)? When do you use Helm vs Kustomize?
44. **What is Kustomize?** How does it differ from Helm?
45. **What are ArgoCD and Flux?** How does GitOps work in an EKS cluster?
46. **What is `eksctl`?** Why is it easier than raw CloudFormation for EKS?
47. **How do you back up and restore a Kubernetes resource?** (Velero, etcd snapshots)
48. **What is etcd and why is it the most critical component of the control plane?**
49. **How does the Cluster Autoscaler or Karpenter work?** When would you choose Karpenter?
50. **How do you implement blue/green or canary on EKS?** (Argo Rollouts, Flagger, weighted ALB targets)
51. **What is a sidecar container and when do you use one?** (service mesh, log shipping)
52. **How do you manage multi-cluster visibility?** (federation, Prometheus Thanos/Mimir)

---
# PART J — CLOUD & AWS

*Your resume lists EC2, EKS, S3, EBS, ALB/ELB, IAM, VPC, Auto Scaling, Lambda, CloudWatch. Each gets real coverage below.*

## EC2
1. ⭐ **How do you connect to an EC2 instance securely?** (SSH key pairs vs Session Manager vs bastion.)
2. ⭐ **What are AMIs? How do you build a custom AMI and reuse it across an Auto Scaling group?**
3. ⭐ **How do you scale EC2 horizontally vs vertically?** What is the difference in downtime and cost?
4. **What is a Security Group vs a NACL vs an IAM policy?** When is each enforced?
5. **What is an Elastic IP and when do you use one?** What is the difference with a Public IPv4?
6. **How do you troubleshoot an instance that won't SSH in?** (SG inbound, subnet route table, key, user)
7. **What is a placement group and why would you use one?**
8. **How do you recover a failed instance?** (replacement policy, health checks)

## EBS & Storage
9. ⭐ **What are the EBS volume types** (gp2, gp3, io1, io2, st1, sc1)? How do they differ in IOPS, throughput, and cost?
10. ⭐ **What is the difference between EBS and S3?** When would you use each?
11. **What is an EBS snapshot and how do you automate backups?** (Data Lifecycle Manager, KMS encryption)
12. **What is the difference between `DeleteOnTermination` and not setting it?**
13. **How do you mount and grow an EBS volume on a running instance?**

## S3
14. ⭐ **What are the different S3 storage classes** and their trade-offs?
15. ⭐ **What is the difference between S3 versioning and object lock?** Why do enterprises enable versioning?
16. **What is an S3 lifecycle policy?** Give an example of transitioning to Glacier after 90 days.
17. **What is the difference between a bucket policy, an ACL, and an IAM policy?** Which wins on conflict?
18. **How do you secure an S3 bucket?** (Block Public Access, encryption, access logs, VPC endpoints)
19. **What is pre-signed URL and when do you use one?**
20. **How do you sync two S3 buckets?** (`aws s3 sync`)

## VPC & Networking
21. ⭐ **Explain the components of a VPC** — subnets, route tables, IGW, NAT GW, VPC endpoints, security groups, NACLs.
22. ⭐ **Draw the path of a request from a pod in a private subnet to an internet API and back.** (NAT GW, route table, IGW, public/private subnets)
23. ⭐ **What is the difference between a public and a private subnet?**
24. **What is a NAT Gateway vs a NAT Instance?** Cost and availability trade-offs.
25. **What are VPC endpoints and why do you use them for S3?** (PrivateLink, avoids IGW)
26. **What is a Transit Gateway?** When would you use it over VPC peering?
27. **How do you connect a VPC to an on-premises data center?** (Direct Connect, VPN)
28. **What is a Network ACL and how does its stateless nature affect return traffic?**

## ELB / ALB
29. ⭐ **What are the three types of load balancers?** (Classic, ALB, NLB) — what protocol, target type, and routing does each support?
30. ⭐ **How does an ALB target group health check work?** What are the key settings?
31. **What is a stickiness session and when is it needed?**
32. **What are the ALB listener rules and path patterns?**
33. **When would you use an NLB over an ALB?** (static IPs, TCP/UDP, high throughput, source IP preservation)

## Auto Scaling
34. ⭐ **What are the components of an Auto Scaling group?** (Launch template, ASG, health checks)
35. ⭐ **What are the scaling policies?** (target tracking, step scaling, scheduled, predictive)
36. **What is the difference between scaling-out and scaling-in?** Why is scale-in harder?
37. **What are lifecycle hooks?** When are they useful?
38. **How do you protect an ASG from accidental termination?** (termination protection)

## IAM
39. ⭐ **What is the difference between a user, role, and policy?** What is an instance profile?
40. ⭐ **What is a trust policy?** Write one that allows an EC2 instance to assume a role.
41. ⭐ **What are the different IAM policy types?** (identity-based, resource-based, SCP, permission boundary, session policy)
42. **What is the principle of least privilege, and how do you enforce it technically?**
43. **How do you grant cross-account access?** (role + trust relationship)
44. **How do you troubleshoot "Access Denied"?** (policy, SCP, permission boundary, explicit deny)
45. **What is IAM Access Analyzer and least-privilege policy generation?**

## Lambda
46. ⭐ **What triggers a Lambda function?** What are the limits you have to design around?
47. ⭐ **How do you pass secrets to Lambda?** (Environment variables from Secrets Manager, or a role)
48. **What is the cold start problem and how do you mitigate it?** (provisioned concurrency, SnapStart, smaller packages)
49. **How do you make a Lambda idempotent?** Why does it matter?
50. **What is the difference between Lambda and a container on Fargate?**

## CloudWatch
51. ⭐ **What is the difference between CloudWatch metrics, logs, and alarms?**
52. ⭐ **How do you create a custom CloudWatch metric?** When would you publish one?
53. **What is a CloudWatch alarm and what happens when it goes into ALARM?** (SNS, auto-scaling action)
54. **What is a composite alarm and why use one?**
55. **How do you aggregate metrics across 400+ instances?** (Metric math, dimension filters, resource groups)
56. **What are CloudWatch Logs Insights queries?** Give an example.
57. **What is the retention period on logs and how does it affect cost?**

## EKS (AWS-specific)
58. ⭐ **What managed components does EKS give you?** (control plane, node groups, add-ons: VPC CNI, CoreDNS, kube-proxy, ALB controller, EBS CSI, Secrets Store CSI)
59. ⭐ **How do EKS node groups pick up AMI/instance type updates?** (AMI type: AL2 x86/AL2023, GPU, Bottlerocket)
60. **How do you enable IRSA for a service account?**
61. **How do you pull images from a private ECR in an EKS cluster?**
62. **What is the EKS access entry API and how does it differ from aws-auth ConfigMap?**
63. **How do you upgrade an EKS add-on?** What happens if the version is too old?

---
# PART K — TERRAFORM & INFRASTRUCTURE AS CODE

1. ⭐ **What are the three phases of Terraform?** (`init`, `plan`, `apply`) What does each actually do?
2. ⭐ **What is state?** Why is it the most important concept in Terraform? Where should it live in a team?
3. ⭐ **What happens if two engineers run `apply` concurrently?** What is state locking and how do you enable it?
4. ⭐ **Explain the difference between `terraform plan` and `terraform apply -auto-approve`.** Why is reviewing the plan mandatory in production?
5. ⭐ **What is a Terraform module?** Explain `variables`, `outputs`, `main.tf`, `providers.tf`, `versions.tf`.
6. ⭐ **What are the variable types** — `string`, `number`, `bool`, `list`, `map`, `object`, `set`? When would you use each?
7. ⭐ **What is `count` vs `for_each`?** When does `count` cause problems?
8. **What is `depends_on` and when is it required?**
9. **What is the difference between `local`, `variable`, and `data` blocks?**
10. **How do you manage sensitive values?** (`sensitive = true`, why not to put secrets in state, remote state encryption)
11. **What is a remote backend?** Which backend do you use for a team and why?
12. **What happens if you lose state?** What are the recovery options?
13. **What are provider version constraints and `terraform init -upgrade`?**
14. **What is `terraform import` and when is it the only option?**
15. **How do you do a targeted apply to a single resource?** (`-target` — and when is it dangerous?)
16. **What is `terraform taint` / `untaint` and `terraform replace`?**
17. **How do you structure Terraform for multiple environments?** (workspaces vs separate state vs Terragrunt)
18. **How do you prevent manual console changes?** (drift detection, policies)
19. **What is drift and how do you detect it in CI?**
20. **What are Terraform Cloud / Terraform Enterprise and what do they add?**
21. **How do you write a reusable module for an EKS cluster?** (what are the inputs and outputs?)
22. **How do you tag resources?** Why does tag-based cost allocation matter?
23. **What is the difference between `terraform destroy` and just deleting the resources?** Why avoid destroy in prod?
24. **How do you handle secrets that must exist before Terraform runs?** (data sources, Secrets Manager, external provider)

---

# PART L — CI/CD PIPELINES (JENKINS & GITHUB ACTIONS)

## Jenkins
1. ⭐ **What is Jenkins and what are agents, controller, and executors?**
2. ⭐ **What is a Jenkinsfile?** Explain `stages`, `steps`, `agent`, `environment`, `post`, `parameters`.
3. ⭐ **What is declarative vs scripted pipeline syntax?** When would you use each?
4. ⭐ **How do you handle credentials in Jenkins?** (credentials binding, why not plain text)
5. ⭐ **What are pipeline stages you'd build for a Java microservice?** (Checkout → Build → Unit Test → SAST/SCA → Docker build → Push → Deploy staging → Smoke → Deploy prod → Verify)
6. **What is a multibranch pipeline?** How does it work?
7. **What is a shared library?** Why use one?
8. **How do you parameterize a pipeline?** (string, boolean, choice, file parameters) What are the security implications of allowing a user to pass a shell command?
9. **What is a webhook trigger and how do you secure it?**
10. **How do you run a matrix build?** (Jenkins matrix axis, e.g. across OS or Java versions)
11. **What is Blue Ocean and what problem does it solve?**
12. **How do you control concurrent builds?** (`disableConcurrentBuilds`)
13. **How do you back up Jenkins and its configuration?**
14. **How do you set up agents** — inbound vs outbound, and what are the security implications of outbound?
15. **What are the steps to install a JDK and Maven tool on a Jenkins agent?**
16. **How do you roll back a bad pipeline change?** (pipeline as code in git, `REPLAY`/`RETRY`)
17. **What is a Jenkins pipeline library vs a shared library?** (clarify the term)

## GitHub Actions
18. ⭐ **What is a workflow, and where does it live?** What triggers it?
19. ⭐ **Explain `jobs`, `steps`, `runs-on`, `uses`, and `run`.**
20. ⭐ **How do you pass artifacts and values between jobs?** (`actions/upload-artifact`, `outputs`, `needs`)
21. **What are `services` containers and when do you use them?** (e.g. a Postgres container for integration tests)
22. **What are `environment` and `environment: url`?** What protections can you set?
23. **What is a reusable workflow?** How do you call one?
24. **How do you use matrix builds?** (OS, node version, language version)
25. **What are the security implications of `pull_request_target`?** Why is it dangerous?
26. **How do you use OIDC to authenticate to AWS without long-lived keys?**
27. **What is a self-hosted runner and what are its risks?**
28. **How do you set up a required status check to block a merge?**
29. **What is a concurrency group and why would you use it?** (prevent parallel deploys to the same environment)
30. **How do you cache dependencies in GitHub Actions?** (`actions/cache`, key strategy)

## Shared CI/CD Concepts
31. ⭐ **What is a quality gate?** Where do you put it in the pipeline?
32. ⭐ **What are SAST, DAST, SCA, and container scanning, and where does each fit?**
33. **What is blue/green deployment and how do you implement it in CI/CD?**
34. **What is canary deployment and what metrics do you watch before promoting?**
35. **How do you handle database schema changes in a CI/CD pipeline?** (expand-and-contract, backward-compatible migrations)
36. **How do you implement a rollback in a pipeline?**
37. **What is a monorepo vs polyrepo from a CI/CD perspective?**
38. **How do you prevent one team's pipeline from breaking another?** (isolation, shared library versioning)
39. **What is pipeline as code and why is it important?**
40. **How do you measure pipeline performance?** (build time, queue time, success rate)

---

# PART M — MONITORING & OBSERVABILITY

*Resume tools: Prometheus, Grafana, CloudWatch, Splunk, OEM (Oracle Enterprise Manager), Observe*

## Prometheus & Grafana
1. ⭐ **What is Prometheus?** Explain the pull model, the scrape interval, and why it fits Kubernetes.
2. ⭐ **What are the four metric types** — counter, gauge, histogram, summary — and how do they differ?
3. ⭐ **Write a PromQL query** for the 99th percentile latency over 5 minutes.
4. ⭐ **Explain `rate()` vs `irate()` vs `increase()`.** Give an example where they differ.
5. ⭐ **What is a recording rule and when do you use one?**
6. **What is an alerting rule and how does Prometheus Alertmanager work?** (grouping, inhibition, routing, silences)
7. **What is `up` and how do you use it?** (target availability)
8. **What are the built-in Kubernetes metrics?** (`kube_pod_cpu_usage_seconds_total`, `kube_pod_memory_working_set_bytes`, etc.)
9. **What is an exporter?** (node_exporter, kube-state-metrics, blackbox_exporter, JMX exporter)
10. **What is the JMX Exporter and how do you expose JVM metrics to Prometheus?**
11. **How do you configure Prometheus for a Kubernetes cluster?** (ServiceMonitor, PodMonitor, Prometheus Operator)
12. **What is remote write and why do you need long-term storage?**
13. **What is Thanos or Mimir and what problem do they solve?**
14. **How do you correlate metrics, logs, and traces?** (exemplars, trace IDs in logs)
15. **What is a Grafana dashboard and what makes a good one?** (golden signals)
16. **How do you use Grafana templating variables?**
17. **How do you write and run a `promtool` unit test for a rule?**
18. **What are the four golden signals?** (latency, traffic, errors, saturation)
19. **What is the difference between monitoring and observability?** Why does it matter for alerting design?
20. **How do you decide what to alert on vs what to put on a dashboard?**

## CloudWatch
21. ⭐ **What are the CloudWatch metrics namespaces?** (AWS/EC2, AWS/EKS, AWS/ELB, AWS/RDS)
22. ⭐ **How do you create an alarm and what actions can it trigger?**
23. **What is a composite alarm and when do you use one?**
24. **What is CloudWatch Logs Insights?** Give a useful example query.
25. **How do you aggregate instance-level metrics into a fleet-wide view?**
26. **What is an anomaly detector?**
27. **How do you control CloudWatch cost?** (retention, log filters, metric filters)

## Splunk
28. ⭐ **What is Splunk and what problem does it solve?** (log aggregation, search, dashboards)
29. **What is an index, a sourcetype, and a search head?** (splunk architecture basics)
30. **What is SPL?** Write a search to count errors by service in the last hour.
31. **How do you get logs into Splunk from Kubernetes?** (Fluent Bit / Splunk OTel Collector)
32. **What is a Splunk dashboard and what are its key components?**
33. **How do you create an alert in Splunk?** (saved search + scheduled + action)
34. **What is the difference between Splunk Enterprise and Splunk Cloud?**
35. **How do you control Splunk index size?** (retention, archiving)
36. **What are Splunk heavy forwarders and what are they for?**

## OEM (Oracle Enterprise Manager)
37. **What is Oracle Enterprise Manager?** What does it manage and monitor?
38. **What is an Oracle Management Agent and a Management Repository?**
39. **How do you monitor a WebLogic/WebSphere target in OEM?** (JMX, agents, plug-ins)
40. **What is OEM Cloud Control and how does it differ from classic OEM?**
41. **How do you create an alert in OEM and have it notify the right team?**
42. **What is a diagnostic/administrative task in OEM?**

## Observe (Observe Inc / ObserveNow)
43. **What problem does Observe solve vs Prometheus/Grafana?** (high-cardinality, correlation of logs/metrics/traces)
44. **How do you model telemetry in Observe?** (observability pipelines, datasets, sources)
45. **What is cardinality and why is it a problem for Prometheus at scale?**
46. **How do you build a dashboard in Observe?** (boards, panels, variables)
47. **How does Observe handle alerts and incidents?**
48. **When would you choose Observe over a classic Prometheus + Grafana stack?**

## General SRE
49. ⭐ **What are the four golden signals and how do you alert on each?**
50. ⭐ **What is an SLO and an error budget?** How does the error budget drive release decisions?
51. **What is a burn rate alert and why is it better than a naive threshold?**
52. **What is the difference between a static threshold and a dynamic/adaptive threshold?**
53. **How do you design an alert that is actionable?** (runbook link, clear impact, no duplicate noise)
54. **What is alert fatigue and how do you prevent it?**
55. **How do you measure monitoring coverage?** (what fraction of services have SLOs, dashboards, alerts)
56. **What is a health check vs a liveness check in the context of alerting?**

---
# PART N — MESSAGING (KAFKA & WEBSPHERE MQ)

## Apache Kafka
1. ⭐ **What are the core components of Kafka?** (broker, topic, partition, producer, consumer, consumer group, ISR, controller)
2. ⭐ **Explain partitioning.** How does it affect ordering, parallelism, and throughput?
3. ⭐ **What is a consumer group and how does rebalancing work?** What is consumer lag and how do you reduce it?
4. ⭐ **What are the different `acks` settings?** (`0`, `1`, `all`) What is the durability trade-off of each?
5. ⭐ **What is the replication factor and min.insync.replicas?** What happens if a broker fails?
6. **What is `retention`?** (`log.retention.hours`, `log.retention.bytes`, cleanup.policy)
7. **What is the difference between a topic and a partition?** How do you pick a partition count?
8. **What is an offset?** How does a consumer resume from where it left off?
9. **What are the delivery semantics?** (at-most-once, at-least-once, exactly-once)
10. **How do you achieve exactly-once processing?** (idempotent producer + transactions)
11. **What is `log.retention.bytes` vs `log.retention.hours`?** Which wins?
12. **What is a partition leader and how is it elected?** (KRaft vs ZooKeeper)
13. **What changed in Kafka 3.x / 4.x with KRaft?** Why does ZooKeeper removal matter operationally?
14. **How do you monitor Kafka?** (under-replicated partitions, ISR shrinkage, consumer lag, request latency)
15. **What is `log.flush.interval.messages` vs `flush.ms`?** What does it mean for throughput?
16. **How do you rebalance a partition away from a broker?** (`kafka-reassign-partitions.sh`)
17. **What is a Schema Registry and why does it matter for schema evolution?**
18. **How do you handle a poison pill message?**
19. **What are the security options?** (SASL/PLAIN, SCRAM, SSL, ACLs)
20. **How do you expand a Kafka cluster without downtime?**

## IBM WebSphere MQ
21. ⭐ **What are the MQ objects?** (queue manager, queue, topic, channel, queue manager group)
22. ⭐ **What is a queue and a topic in MQ?** What is the difference in delivery semantics (point-to-point vs pub/sub)?
23. ⭐ **What is a channel and what types exist?** (sender, receiver, requester, cluster)
24. ⭐ **What is a dead-letter queue and when does a message land there?**
25. **What is a back-stop / back-out threshold?**
26. **How do you monitor MQ?** (MQ Explorer, `runmqsc`, PCF commands, queue depth alerts)
27. **What are the common MQ troubleshooting steps?** (channel status, queue depth, dead letters, listener status)
28. **What is the difference between a cluster and a queue manager group?**
29. **What is MQ's transactional messaging / commit and rollback?**
30. **How do you do a put/get test with `amqput`/`amqget`?**
31. **What is a listener and what happens if it goes down?**
32. **How do you upgrade MQ and what are the pre-req checks?** (`PRECHECK`, `OCC`)
33. **What are MQ security concepts?** (channels, SSL, OCSL for auth, users on the QM)

---

# PART O — MIDDLEWARE (WEBSPHERE, WEBLOGIC, JBOSS, TOMCAT, IBM HTTP SERVER)

*Your middleware experience across 200+ instances is a strong differentiator — expect real scenario questions.*

## WebSphere Application Server (IBM)
1. ⭐ **What are the components of WebSphere ND?** (DMGR, Node Agents, Application Servers, Deployment Manager)
2. ⭐ **Explain the WebSphere configuration model** — cells, nodes, servers, clusters, and what a `configChange` actually does.
3. ⭐ **What is a virtual host and a server group?** How does a request get routed?
4. ⭐ **What are the JVM options you'd tune on WebSphere?** (heap, metaspace, GC, thread pools)
5. **What is a WAS Liberty profile and how does it differ from Traditional/ND?**
6. **What is the difference between a Deployment Manager and a standalone server?** Why does it matter for DR?
7. **How do you deploy an application in WebSphere?** (console, wsadmin, `installapps`, application server restart)
8. **What are application server scopes?** (cell, node, cluster, server) How does scope affect a variable?
9. **What is `server.xml` / `bootstrap.properties` / `jvm.options`?** Where do you find them and what goes in each?
10. **How do you capture a heap dump in WebSphere?** (wsadmin, jcmd, kill -3, IBM diagnostics)
11. **What is the WebSphere "Pluggable" vs "Standalone" installation?**
12. **How do you handle a hung application server?** (`kill -3` for a thread dump, then `ce`)
13. **What is "Tune IBM HTTP Server" and why is IHS often used?**
14. **How do you do rolling upgrades in a WebSphere cluster?**
15. **What are the health checks in the WAS console?** (e.g. "Run All Plugin Configuration Steps")

## WebLogic
16. ⭐ **What is a WebLogic domain, server, cluster, and managed server?**
17. ⭐ **What is a WebLogic deployment mode?** (Admin Server + Managed Servers vs Domain)
18. **What is a JDBC connection pool and what happens if it can't connect to the DB?**
19. **How do you tune WebLogic?** (WorkManager threads, Stuck Thread Detection, max message size)
20. **What are Stuck Threads and how do you find them?** (WebLogic thread dumps, WLS stuck thread)
21. **How do you change WebLogic config in production?** (WLST / `config.sh` — and why not by hand)
22. **What is a WebLogic cluster and how does it do session replication?**
23. **How do you restart a managed server safely?** (graceful vs forced shutdown)
24. **What is the role of the WebLogic Diagnostic Advisor?**

## JBoss / WildFly
25. ⭐ **What are the main JBoss/WildFly modes?** (standalone vs domain, and the old "standalone, HA, full-profile")
26. **What is `standalone.conf` vs `domain.xml`?** Where do you set JVM options?
27. **How do you configure a datasource in JBoss?**
28. **What is JBoss Management / admin console access?** (management port, RBAC roles)
29. **How do you deploy an application?** (CLI `jboss-cli`, filesystem deployment scanner, management API)
30. **What are the differences between WildFly and JBoss EAP?**

## Tomcat
31. ⭐ **What are the core Tomcat components?** (Connector, Engine, Host, Context, Valves, AccessLogValve)
32. ⭐ **What is `server.xml`, `web.xml`, and `context.xml`?** Where do you change the connector port vs the thread pool?
33. **How do you tune Tomcat's thread pool?** (`maxThreads`, `minSpareThreads`, `acceptCount`) What happens when maxThreads is hit?
34. **How do you configure Tomcat's HTTPS connector?** (keystore, `server.xml` SSLHostConfig)
35. **How do you deploy an application to Tomcat?** (WAR drop, exploded dir, Tomcat Manager)
36. **What is the default JVM heap for Tomcat and how do you change it?** (`setenv.sh`)
37. **How do you read Tomcat's logs and access logs?** (`catalina.out`, `localhost.*.log`, `access_log*`)
38. **What are the common Tomcat tuning knobs for production?**

## IBM HTTP Server (IHS) & AHS
39. **What is IHS and why is it used in front of WebSphere?**
40. **What is the `httpd.conf` structure and the difference between a `<VirtualHost>` and `<Server>`?**
41. **How do you configure SSL in IHS?** (`mod_ibm_ssl`, KeyFile, SSLEnable, certificate directives)
42. **What is the difference between IHS and Apache HTTP Server?** (IBM's derivative, mod_ibm_ssl vs mod_ssl)
43. **What is a proxy pass / `ProxyPass` / `ProxyPassReverse`?** (WebSphere Plugin routing to app servers)
44. **What is the WebSphere Plug-in and `plugin-cfg`?** Why does it need regenerating?
45. **What is AHS (Apache Http Server) and how does it relate to IHS?**
46. **How do you rotate an SSL certificate in IHS without downtime?**

## Cross-Middleware / Ops
47. ⭐ **What are the shared JVM tuning parameters across all these app servers?** (Xms/Xmx, Metaspace, GC selection, thread stack size)
48. ⭐ **How do you troubleshoot a Java app server under memory pressure?** (heap vs metaspace vs native memory)
49. **What is a thread pool exhaustion scenario and how do you identify it from a thread dump?**
50. **How do you do a rolling restart of a middleware cluster with zero downtime?** (drain, stop, patch, start, verify, drain next)
51. **How do you back up a middleware configuration?** (WebSphere `configBackup`, WebLogic backup script, Tomcat conf copy)
52. **What is the DR procedure for an app server cluster?** (cell config, MQ, database, and the order to restore)
53. **How do you automate middleware deployments?** (Ansible, WLST, wsadmin, `installapps`) — what have you scripted?
54. **What is a maintenance window and how do you plan one for 200+ instances?**
55. **How do you handle a version upgrade across 200+ middleware instances?** (pilot → canary → waves, rollback plan)

---

# PART P — SECURITY & IAM (RESUME-SPECIFIC)

*Resume lists: SSL/TLS, LDAP, TAM, TDS, IKeyMan, IAM, IBM ISAM*

## SSL/TLS
1. ⭐ **What happens during the TLS handshake?** Explain the key exchange, the CA's role, and where asymmetric vs symmetric encryption is used.
2. ⭐ **What is a certificate chain and what does "expired" actually break?** How do you find every place a cert is installed?
3. ⭐ **How do you renew a certificate without downtime?** (CSR → CA → new cert → graceful reload → verify → swap)
4. **What is the difference between a wildcard and a SAN certificate?**
5. **What is the difference between SSLv3, TLS 1.0/1.1/1.2/1.3?** Why are older versions deprecated?
6. **How do you configure TLS in Nginx / IHS / Tomcat / a Spring app?** (keystore type, protocol versions, cipher suites)
7. **What is a self-signed vs CA-signed certificate and when is each acceptable?**
8. **How do you set up certificate monitoring and alerting?** (expiry threshold alerts)
9. **What is certificate pinning and why do mobile apps use it?**

## LDAP / Directory
10. ⭐ **What is LDAP and what are the core concepts?** (DIT, DN, entries, attributes, objectClass)
11. ⭐ **What is the difference between a bind DN and a user bind?** Why do you need a service account for search?
12. **What is LDAP search?** Explain filter syntax and the difference between a base, one-level, and subtree search.
13. **How do you integrate LDAP with an application for authentication and authorization?** (group-to-role mapping)
14. **What are LDAPS and StartTLS, and why is plain LDAP over the network a problem?**
15. **What is an LDAP referral and when do you see them?**
16. **How do you troubleshoot an LDAP bind failure?** (bind DN wrong, password, TLS, base DN, server reachability)
17. **What is the difference between LDAP and Active Directory from an ops view?**
18. **How do you manage LDAP replication and failover?**

## IBM Tivoli Access Manager (TAM)
19. **What is IBM TAM and what problem does it solve?** (centralized web authentication / SSO)
20. **What are the components?** (Policy Server, WebSEAL, user registry)
21. **What is WebSEAL and how does it protect a backend application?**
22. **What is a protection policy / junction / application object in TAM?**
23. **How does TAM integrate with LDAP?** (user registry)
24. **What are common TAM operational issues?** (policy cache, authentication failures, failover)
25. **How do you onboard a new application behind TAM?**

## IBM Tivoli Directory Server (TDS)
26. **What is IBM TDS and what does it add over a standard LDAP server?**
27. **What are the TDS components?** (server, database, instance, administrative server)
28. **How do you back up and restore a TDS database?**
29. **What is TDS `ldif2db` / `db2ldif` and why do you use them for bulk changes?**
30. **How do you tune TDS?** (caching, connection pool, indexes)
31. **What are common TDS troubleshooting areas?** (dbspace, lock manager, replication)

## IBM iKeyMan
32. **What is iKeyMan and what does it manage?** (SSL certs, keys, keystores)
33. **How do you list and manage certificates in iKeyMan?** (Key Management Application)
34. **How do you export a key from iKeyManager for use in a keystore?**
35. **What is the difference between a CMS keystore and a JKS keystore, and how do you convert?**
36. **How do you automate certificate rotation with iKeyMan?** (command line, SKI tools)

## IBM Identity and Access Management (IAM)
37. ⭐ **What does IAM cover?** (authentication, authorization, identity lifecycle, governance)
38. **What is the difference between authentication and authorization?** Give IAM examples of each.
39. **What is RBAC vs ABAC vs policy-based access control?**
40. **What is an identity provider (IdP) and a service provider (SP)?** (SSO, SAML, OIDC, OAuth 2.0)
41. **What is the difference between OAuth 2.0 and OIDC?** What problem does OIDC add?
42. **What is a JWT and what claims does it carry?**
43. **How do you implement least-privilege access for a human user?** (JIT access, PAM, role-based approval)
44. **What is PAM (Privileged Access Management) and why does it matter?**

## IBM ISAM / Security Verify Access
45. **What is IBM ISAM (Security Verify Access) and what are its components?** (Policy Server, WebSEAL, authentication service)
46. **How does ISAM differ from TAM?** (evolution, additional factors, federation)
47. **What are the OAuth/OIDC capabilities in ISAM?** (API gateway functions)
48. **How do you federate identity to a third-party IdP?**
49. **What is risk-based access in ISAM and how is it configured?**
50. **How do you audit access in ISAM?** (log, audit trail)

## General Security for DevOps
51. ⭐ **What is the CIA triad and how does it apply to a DevOps role?**
52. **What is a secret and how should it be managed?** (rotation, least privilege, audit)
53. **What is network segmentation and how does it reduce blast radius?**
54. **What is a vulnerability vs a threat vs a risk?**
55. **How do you keep secrets out of Git?** (pre-commit scanning, secret scanning, `.gitignore`)
56. **What is supply-chain security for containers?** (signed images, SBOM, pinning digests, provenance)
57. **What is a CVE, and what do you do when a Critical CVE appears in a base image?**
58. **How do you implement audit logging for a production change?**
59. **What is the principle of least privilege, and how does it change your daily DevOps work?**

---
# PART Q — IT SERVICE MANAGEMENT TOOLS (SERVICENOW, REMEDY, JIRA)

## ServiceNow
1. ⭐ **What is ServiceNow and what are its core modules?** (Incident, Problem, Change, CMDB, Request, Knowledge, Asset)
2. ⭐ **Explain the difference between Incident and Problem management.** How do they relate?
3. ⭐ **What is a Change Request and what is the CAB process?** What are the change types (Standard, Normal, Emergency)?
4. ⭐ **What is the CMDB and why is it called the "single source of truth"?** What is a CI?
5. **How do you use ServiceNow for on-call rotation?** (Schedule, Assignment, Notifications)
6. **What is a Change Advisory Board and how do you get a change approved?**
7. **What are Impact and Urgency, and how do they map to Priority?** What is Priority 1 vs Priority 2?
8. **How do you create a knowledge article and why does it matter?** (KEDB — Known Error Database)
9. **What is a Virtual Agent or Walk-up in ServiceNow?**
10. **How do you write a notification or approval workflow?**
11. **What is SLA management and how do you measure SLA compliance?**
12. **How do you integrate ServiceNow with monitoring tools?** (Event Management / Event API)
13. **What is the difference between a catalog item and a record?**
14. **How do you handle major incident management in ServiceNow?**
15. **What are the practical parts of ServiceNow scripting?** (GlideRecord, business rules, flows)

## Remedy (BMC Remedy)
16. ⭐ **What is BMC Remedy and what is ITSM?** (incident, problem, change, CMDB, SRM)
17. ⭐ **How does Remedy's incident model work?** (Impacted CI vs Affected CI — the classic differentiator)
18. ⭐ **What are the BMC Remedy applications?** (Incident Management, Problem Management, Change Management, Service Desk)
19. **What is the difference between BMC Remedy ITSM and ServiceNow from an ops perspective?** (config-driven vs form/process-driven, ARs)
20. **What is an Assignment and an Assignment Group in Remedy?** How do you route?
21. **How do you use Remedy for change management and approvals?**
22. **What are the key tables in Remedy?** (Problem, Incident, Change Request, CI, Groups, Assignments)
23. **How do you run BMC Remedy ADSM/Knowledge management for post-incident reviews?**
24. **How do you integrate Remedy with monitoring?** (Event Management, from Megahelp)

## Jira
25. ⭐ **What is Jira and what are its core issue types?** (Story, Bug, Task, Epic, Sub-task)
26. ⭐ **What is a Jira workflow?** How do you design one?
27. **What is Jira Software vs Jira Service Management?** (SD: incident, request, SLA)
28. **How do you use Jira for incident management?** (JSM vs PagerDuty vs ServiceNow)
29. **What are sprints and the Agile boards?** (Scrum vs Kanban)
30. **What is a Jira filter, saved search, and dashboard?**
31. **How do you link Jira issues to CI/CD builds?** (deployment info, commit hashes, smart commits)
32. **How do you write a good bug report from a production incident?**
33. **What is Jira automation and what can you automate?** (rules, workflows, notifications)
34. **How do you manage Jira permissions and project roles?**
35. **What is a post-incident review (PIR) in Jira?** How do you run one?

---
# PART R — DEEP DIVES ON *YOUR* RESUME

*These are the questions an interviewer will ask **because** they read your resume. Each bullet on your resume is a claim — be ready to defend it with specifics.*

## R1. Your headline numbers (you must defend every one)

1. ⭐ **"You say you cut release cycle time by 35%. What was the baseline, how did you measure it, and what specifically did you change to get there?"**
   *Prepare: the original release process (how many manual steps, how many days), the pipeline stages you added, the tooling, and the measurement window. Be ready to admit it was an estimate rather than a formal metric.*

2. ⭐ **"Provisioning went from days to under 45 minutes. Walk me through exactly what Terraform modules you wrote."**
   *Prepare: the module layout (VPC, EKS, ALB, IAM), how you handled multi-region, and how you avoided the state-file collision problem.*

3. ⭐ **"MTTD reduced by 30% — how did you even measure MTTD before and after?"**
   *Prepare: your detection source (Prometheus/CloudWatch alerts), how you tracked alert-to-acknowledgement, and what specific alerting change made the difference.*

4. ⭐ **"40% reduction in manual operational effort from shell automation. What specifically did you automate?"**
   *Prepare: name the scripts (health checks, log rotation, patching), how they were scheduled (cron), and how you made them safe across 400+ servers.*

5. ⭐ **"MTTR improved 25% using heap/thread dumps. Walk me through a real OOM or deadlock incident end to end."**
   *Prepare: the symptom → alert → triage → dump analysis → root cause → fix → prevention. Be ready to explain what you found in the dump.*

6. ⭐ **"99.9% uptime across 200+ middleware instances — how was that calculated, and what uptime did you actually have?"**
   *Prepare: the source (monitoring, OEM/Splunk), the calculation window, and honestly what the number was.*

7. **"15+ Java microservices on Jenkins and GitHub Actions — did you use both, or did one win?"**
   *Prepare: this is a great question. Say which pipeline owned what (e.g., Jenkins for legacy/middleware, GHA for containerized services) and why.*

## R2. Worldpay (current role, May 2025 – present)

8. ⭐ **"Tell me about the multi-region AWS infrastructure you provisioned. What regions, and how did you handle failover?"**
9. ⭐ **"You deployed to EKS. What did you use for ingress, secrets, and image pulls? How did you handle cross-region services?"**
10. ⭐ **"How did you run rolling updates on a production workload without downtime?"**
11. **"How did you structure RBAC across your EKS clusters?"**
12. **"What does your Prometheus/Grafana setup look like in production — scrape interval, retention, cardinality?"**
13. **"How do you do deployment validation and health checks across 400+ production servers?"**
14. **"Walk me through your RCA process."**
15. **"What was your most challenging production incident and how did you resolve it?"**

## R3. TCS (Dec 2021 – May 2025)

16. ⭐ **"You administered WebSphere across 200+ instances. How did you manage configuration drift across so many servers?"**
17. ⭐ **"How did you do a rolling upgrade of 200+ middleware instances with zero downtime?"**
18. **"How did you diagnose the OOM / thread deadlock / GC latency incidents? What was the actual root cause?"**
19. **"How did you perform JVM tuning? What were the before/after heap sizes and GC settings?"**
20. **"How did you handle Java upgrades and production hardening?"**
21. **"What was your SSL certificate management process? How did you avoid expiry outages?"**
22. **"How did you automate server patching, and how did you ensure it was safe?"**
23. **"How did you do DR activities? What was the RTO/RPO and what did you actually do?"**
24. **"What was your capacity planning process for Linux servers?"**
25. **"You used Shell + cron. How did you monitor your own automation for failures?"**

## R4. Cross-cutting scenario questions (the ones that separate candidates)

26. ⭐ **"A P1 just fired: 30% of production requests are failing on a Kubernetes service. Walk me through, minute by minute, what you do."**
   *Testing: order of operations — triage, blast radius, mitigation vs root cause, comms, rollback, RCA.*

27. ⭐ **"Your Terraform state file was corrupted. What do you do?"**
28. ⭐ **"A developer pushed a bad image to production and it took down 10 microservices. What went wrong in your pipeline, and how do you fix it?"**
29. ⭐ **"How would you introduce GitOps to an organization that has never used it?"**
30. ⭐ **"You need to deploy to 3 new AWS regions in 2 weeks. Design the Terraform structure."**
31. **"How do you migrate 200+ on-prem middleware servers to containers without a big bang?"**
32. **"Your CI pipeline takes 45 minutes. How do you get it under 10?"**
33. **"How do you handle a security incident where a certificate was leaked?"**
34. **"Explain a time you had to push back on a delivery deadline. What did you do?"**
35. **"How do you keep 400+ server scripts in sync? How do you version them?"**
36. **"What's your approach to documentation so that someone else could do your job?"**
37. **"A team member says the pipeline is too slow and wants to skip tests. How do you handle it?"**
38. **"How do you balance speed to market against reliability at a bank?"**
39. **"What would you change about your current setup if you joined a company tomorrow?"**
40. **"Where do you see yourself in 3 years? What do you want to be doing?"**

## R5. Behavioral & situational (standard DevOps hiring loop)

41. ⭐ **"Tell me about a time you had a production outage. What was your role?"**
42. ⭐ **"Describe a situation where you had to learn a new technology quickly."** (Your civil engineering background → cloud transition makes a great story.)
43. **"Give an example of automating a repetitive task. What was your approach?"**
44. **"How do you handle disagreement with a developer about a deployment?"**
45. **"Describe a time your monitoring missed something. What did you change?"**
46. **"Tell me about a time you made a mistake in production. How did you handle it?"**
47. **"How do you explain a technical concept to a non-technical stakeholder?"** (e.g., explaining a Kubernetes migration to a business owner)
48. **"What is a weakness you are working on?"**
49. **"How do you handle on-call stress?"**
50. **"Why are you leaving / why do you want this role?"**

## R6. Certifications — expect a quick check

51. **"You hold AWS Cloud Practitioner. How did you prepare, and how has it helped?"**
52. **"Your Kafka admin cert — what did it cover, and where have you applied it hands-on?"**
53. **"Do you plan to pursue AWS Solutions Architect or Kubernetes CKA?"**

---

# PART S — QUICK-FIRE ROUND (rapid-fire, 30 seconds each)

*Interviewers often end with a rapid-fire round. These are short, factual, and quick — you should be able to answer each in one breath. Don't over-explain.*

1. What port does HTTPS use? → 443
2. What port does SSH use? → 22
3. What port does PostgreSQL use? → 5432
4. What port does MySQL use? → 3306
5. What port does Kafka use? → 9092
6. What port does ZooKeeper use? → 2181
7. What port does Elasticsearch use? → 9200
8. What port does Redis use? → 6379
9. What is the default Kubernetes health check port for a pod? → 8080
10. What is `kubectl` shortname for delete? → `del`
11. What is `kubectl` shortname for describe? → `desc`
12. What does `kubectl get pods -o wide` add? → Node, IP, nominated node
13. What is the Kubernetes default namespace? → `default`
14. What is a Kubernetes taint used for? → Repel pods from nodes
15. What is `taint` / `toleration` / `nodeAffinity`? → Scheduling control
16. What command lists Docker containers? → `docker ps`
17. What removes a stopped container? → `docker rm`
18. What is the Docker default bridge network name? → `bridge`
19. What is the difference between `docker exec` and `docker attach`? → New process vs main process
20. What does `docker system df` show? → Disk usage
21. What is the Terraform command to destroy? → `terraform destroy`
22. What is `terraform fmt`? → Format
23. What is `terraform validate`? → Check syntax/config
24. What is `terraform show`? → Show state or plan
25. What is `terraform refresh` deprecated in favor of? → `terraform plan -refresh-only`
26. What is a Jenkins `.groovy` vs `Jenkinsfile`? → Scripted vs declarative
27. What does `git shortlog` show? → Commit counts by author
28. What does `git diff --staged` show? → Staged changes
29. What is `git cherry-pick -n`? → Apply without committing
30. What does `mvn -DskipTests` do? → Skip test execution
31. What does `mvn -U` do? → Force update of snapshots
32. What is `mvn dependency:tree` for? → Dependency graph
33. What does `mvn -pl module -am` do? → Build module and its deps
34. What is the Linux command for last 100 lines of a file? → `tail -n 100`
35. What is `grep -c`? → Count matching lines
36. What does `awk '{print $1}'` do? → First whitespace-separated column
37. What does `sed -i` do? → In-place edit
38. What is `xargs -P 4`? → Run 4 in parallel
39. What is `rsync --delete`? → Delete destination files not in source
40. What is `find . -name "*.log" -mtime -1`? → Log files modified in last 24h
41. What does `nc -zv host port` do? → Test TCP connectivity
42. What is `netstat` vs `ss`? → Legacy vs modern netstat
43. What is `/etc/hosts` used for? → Static hostname→IP overrides
44. What does `dig +short` do? → Quick DNS answer
45. What is `ulimit -n`? → Max open file descriptors
46. What is `chmod 755`? → rwxr-xr-x
47. What is `chmod 640`? → rw-r-----
48. What does `sudo -u jenkins` do? → Run as another user
49. What is `crontab -l`? → List cron jobs
50. What is the cron field for "every 5 minutes"? → `*/5 * * * *`
51. What is the Prometheus default scrape interval? → 30s (varies)
52. What is Prometheus port? → 9090
53. What is Grafana port? → 3000
54. What port does the Kubernetes API server serve on? → 6443 (secure)
55. What port does etcd use? → 2379 (client), 2380 (peer)
56. What port does the AWS ALB use? → 80 / 443
57. What is an AWS AZ? → Availability Zone
58. How many AZs does a standard AWS region have? → 6 (most regions)
59. What is the AWS default region? → us-east-1
60. What is an EC2 instance type like `m6i.large`? → Family, generation, size

---

# PART T — FINAL PREPARATION CHECKLIST

## Things to fix on your resume before the interview
- **"DevOps Engineerwith"** — missing space (also on the CONTACT line: "GitHub| LinkedIn").
- Consider naming the scale of "400+ production servers" and "200+ instances" — if they're the same fleet, say so.
- Your summary says "4+ years of IT experience" — your first role starts Dec 2021, so you're at ~4.5 years as of late 2026. That works for a 3–5 year band. Good.
- The gap: **Jun 2020 – Nov 2021** is unexplained. Have a short, honest answer ready (further education, or something you don't want on the resume). Interviewers *will* ask.
- Consider adding a "Projects" section with one end-to-end Terraform + EKS + GitHub Actions example — interviewers love asking about a self-directed project.

## The 12 numbers you must be able to defend cold
| # | Claim | Be ready to explain |
|---|---|---|
| 1 | 35% release cycle time reduction | Baseline, what changed, how measured |
| 2 | 45 min provisioning | Which modules, multi-region strategy |
| 3 | 30% MTTD reduction | Detection source, what alert change did it |
| 4 | 400+ production servers | Which fleet, how you scripted it |
| 5 | 40% manual effort reduction | Which scripts, cron vs scheduler |
| 6 | 25% MTTR improvement | The actual incident, dump analysis |
| 7 | 99.9% uptime on 200+ instances | Measurement source and window |
| 8 | 15+ Java microservices | Which pipeline owned what |
| 9 | 20% cost reduction | (add to resume if true — strong metric) |
| 10 | 99.95% SLA uptime | (add to resume if true) |
| 11 | 30% fewer production incidents | (add to resume if true) |
| 12 | 5+ AWS services | Fine as-is; be ready to expand |

## If they ask "what do you want to do more of?"
Have a real answer. Given your profile, the strongest one is: **"I want to own a platform end to end — the Terraform modules, the EKS clusters, and the golden-signal dashboards — rather than executing individual tickets."** That reads as a 3–5 year engineer ready for a senior step.

## Five questions to ask THEM
1. "What's the current state of your IaC — full Terraform, or a mix with CloudFormation?"
2. "How do you handle Kubernetes upgrades today, and who owns the cluster?"
3. "What's the biggest operational pain point your team has right now?"
4. "How do you do incident response and post-incident reviews?"
5. "What's the on-call rotation like, and how often is it paged?"

## The one-line framing to memorize
> *"I've spent 4 years doing production DevOps in Java-heavy enterprise environments — WebSphere, MQ, banking workloads — and the last year modernizing that with Terraform, EKS, and CI/CD. The combination is rare: I understand the legacy middleware world and I can build the modern platform on top of it."*

That sentence is your differentiator. Lead with it.

---

*Prepared from Sumit Shimpale's DevOps resume. 700+ questions across every tool listed, calibrated for a 3–5 year DevOps Engineer interview.*





