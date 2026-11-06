# Execution limits and long-running work

Use when a call may run long, a document is large, or an integration stops responding. These notes record practical limits; confirm them against the installed integration, because call budgets, threading behaviour and available workers differ.

## Blocking calls

A call that exceeds its timeout is not necessarily cancelled. On the GUI thread it keeps the application busy, and later calls may fail or queue until it finishes. Inspect state with a minimal call, wait outside the application, and do not resubmit the same mutation while the first may still run. Set an explicit budget for known slow GUI work such as saving a large file or tessellating and exporting large shapes, but remember that the client may cut a single call earlier than the tool's own maximum; split the work instead of relying on one long call.

Do not loop point-in-solid or distance queries over complex spline solids on the GUI thread. Each can take a noticeable fraction of a second, so thousands of them can block the application for minutes. Pre-filter pairs with bounding boxes, sample coarsely, test against a cheap analytic or polygonal stand-in for the surface, or move the loop to an isolated worker. Compute a common volume only when the distance is already near zero.

## Large documents

Document size is an execution cost: saving, reloading and recomputing run on the GUI thread. Dense lofts and repeated copies of heavy shells can make a file many times larger than the geometry it describes. Keep heavy intermediate shapes as external BREP or STEP files read through the shape API, keep the live document to the objects the user needs, and prefer fewer, smoother sections or one revolved or swept profile over a dense loft when the form allows. Do not save a large open document inside a call that has only the default budget.

## Background and isolated workers

A long kernel operation in a background thread can hold the interpreter lock. The integration may then fail to start a job, or be slow to report status, although the job continues. Treat a "failed to start" message or a status timeout as unknown, wait, and poll; do not start duplicates.

A separate headless FreeCAD process is the safest place for long Booleans, lofts and BOP checks, because a crash or hang there does not affect the live session. It needs the command-line binary on the machine that runs the integration, which may be absent or off the search path; check before relying on it. Pass inputs as files, print and flush progress after each stage, split work to fit the per-call budget, and write each result as BREP. Read results back into the live document on the GUI thread after checking validity. A headless process does not update an open GUI document, and a file that is open there must not be overwritten.

## Availability

If integration tools are missing in one turn while the server log shows no error, restart or refused connection, do not assume the application crashed; repeat tool discovery later. Where the integration writes logs, read them before blaming the application: a refused connection at startup usually means the add-on's server was not yet running, a shutdown marked intentional means the host restarted the integration, and a version-check timeout at startup means the application was busy.
