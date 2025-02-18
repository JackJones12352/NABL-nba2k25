import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Table, TableHeader, TableRow, TableHead, TableBody, TableCell } from "@/components/ui/table";

export default function Home() {
  const [results, setResults] = useState([
    { team1: "Team A", score1: 100, team2: "Team B", score2: 98 },
  ]);
  const [newResult, setNewResult] = useState({ team1: "", score1: "", team2: "", score2: "" });
  const [teams, setTeams] = useState([
    { name: "Team A", logo: "team-a-logo.png" },
    { name: "Team B", logo: "team-b-logo.png" }
  ]);
  const [prospects, setProspects] = useState([
    { name: "Top Prospect 1", position: "Guard", team: "College A" },
    { name: "Top Prospect 2", position: "Forward", team: "College B" }
  ]);

  const updateField = (field, value) => {
    setNewResult((prev) => ({ ...prev, [field]: value }));
  };

  const addResult = () => {
    setResults([...results, newResult]);
    setNewResult({ team1: "", score1: "", team2: "", score2: "" });
  };

  return (
    <div className="p-6 space-y-6">
      <h1 className="text-3xl font-bold text-center text-red-600">North American Basketball League</h1>
      
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold">Enter Game Results</h2>
          <div className="grid grid-cols-4 gap-2 mt-2">
            <Input placeholder="Team 1" value={newResult.team1} onChange={(e) => updateField("team1", e.target.value)} />
            <Input placeholder="Score 1" value={newResult.score1} onChange={(e) => updateField("score1", e.target.value)} type="number" />
            <Input placeholder="Team 2" value={newResult.team2} onChange={(e) => updateField("team2", e.target.value)} />
            <Input placeholder="Score 2" value={newResult.score2} onChange={(e) => updateField("score2", e.target.value)} type="number" />
          </div>
          <Button className="mt-4" onClick={addResult}>Add Result</Button>
        </CardContent>
      </Card>
      
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold">Game Results</h2>
          <Table>
            <TableHeader>
              <TableRow>
                <TableHead>Team 1</TableHead>
                <TableHead>Score</TableHead>
                <TableHead>Team 2</TableHead>
                <TableHead>Score</TableHead>
              </TableRow>
            </TableHeader>
            <TableBody>
              {results.map((result, index) => (
                <TableRow key={index}>
                  <TableCell>{result.team1}</TableCell>
                  <TableCell>{result.score1}</TableCell>
                  <TableCell>{result.team2}</TableCell>
                  <TableCell>{result.score2}</TableCell>
                </TableRow>
              ))}
            </TableBody>
          </Table>
        </CardContent>
      </Card>
      
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold">Teams</h2>
          <div className="grid grid-cols-2 gap-4">
            {teams.map((team, index) => (
              <div key={index} className="flex items-center space-x-4">
                <img src={team.logo} alt={team.name} className="w-12 h-12" />
                <span>{team.name}</span>
              </div>
            ))}
          </div>
        </CardContent>
      </Card>
      
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold">Top Prospects</h2>
          <Table>
            <TableHeader>
              <TableRow>
                <TableHead>Name</TableHead>
                <TableHead>Position</TableHead>
                <TableHead>Team</TableHead>
              </TableRow>
            </TableHeader>
            <TableBody>
              {prospects.map((prospect, index) => (
                <TableRow key={index}>
                  <TableCell>{prospect.name}</TableCell>
                  <TableCell>{prospect.position}</TableCell>
                  <TableCell>{prospect.team}</TableCell>
                </TableRow>
              ))}
            </TableBody>
          </Table>
        </CardContent>
      </Card>
    </div>
  );
}
# NABL-nba2k25
